---
title: "ALTER SECURITY POLICY (Transact-SQL)"
description: ALTER SECURITY POLICY (Transact-SQL)
author: VanMSFT
ms.author: vanto
ms.date: "05/01/2017"
ms.prod: sql
ms.prod_service: "database-engine, sql-database"
ms.technology: t-sql
ms.topic: reference
f1_keywords:
  - "ALTER_SECURITY_POLICY_TSQL"
  - "ALTER SECURITY POLICY"
  - "ALTER_SECURITY_TSQL"
  - "ALTER SECURITY"
helpviewer_keywords:
  - "ALTER SECURITY POLICY statement"
dev_langs:
  - "TSQL"
ms.assetid: a8efc37e-113d-489c-babc-b914fea2c316
---
# ALTER SECURITY POLICY (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Alters a security policy.  
  
![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```syntaxsql
ALTER SECURITY POLICY schema_name.security_policy_name   
    (  
        { ADD { FILTER | BLOCK } PREDICATE tvf_schema_name.security_predicate_function_name   
           ( { column_name | arguments } [ , ...n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ]  }   
        | { ALTER { FILTER | BLOCK } PREDICATE tvf_schema_name.new_security_predicate_function_name   
             ( { column_name | arguments } [ , ...n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ] }  
        | { DROP { FILTER | BLOCK } PREDICATE ON table_schema_name.table_name }   
        | [ <additional_add_alter_drop_predicate_statements> [ , ...n ] ]  
    )    [ WITH ( STATE = { ON | OFF } ) ]  
    [ NOT FOR REPLICATION ]  
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  

## Arguments
security_policy_name  
The name of the security policy. Security policy names must fulfill the rules for identifiers and must be unique within the database and to its schema.  
  
schema_name  
Is the name of the schema to which the security policy belongs. *schema_name* is required because of schema binding.  
  
[ FILTER | BLOCK ]  
The type of security predicate for the function bound to the target table. FILTER predicates silently filter the rows that are available to read operations. BLOCK predicates explicitly block write operations that violate the predicate function.  
  
tvf_schema_name.security_predicate_function_name  
Is the inline table value function you use as a predicate and that you enforce upon queries against a target table. At most, you can define one security predicate for a particular DML operation against a particular table. Create the inline table value function using the SCHEMABINDING option.  
  
{ column_name | arguments }  
The column name or expression used as parameters for the security predicate function. Any columns on the target table can be used as arguments for the predicate function. Expressions that include literals, built-ins, and expressions that use arithmetic operators can be used.  
  
*table_schema_name.table_name*  
Is the target table for the security predicate. Multiple disabled security policies can target a single table for a particular DML operation, but only one can be enabled at any given time.  
  
*\<block_dml_operation>*  
The particular DML operation for the applied block predicate. AFTER specifies the predicate is evaluated on the row values after the DML operation was carried out (INSERT or UPDATE). BEFORE specifies the predicate is evaluated on the row values before the DML operation is carried out (UPDATE or DELETE). If no operation is specified, the predicate will apply to all operations.  
  
You can't ALTER the operation for an applied block predicate because the operation is used to uniquely identify the predicate. Instead, you must drop the predicate and add a new one for the new operation.  
  
WITH ( STATE = { ON | OFF } )  
Enables or disables the security policy from enforcing its security predicates against the target tables. If not specified the security policy being created is enabled.  
  
NOT FOR REPLICATION  
Indicates the security policy shouldn't be executed when a replication agent modifies the target object. For more information, see [Control the Behavior of Triggers and Constraints During Synchronization &#40;Replication Transact-SQL Programming&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
table_schema_name.table_name  
Is the target table for the applied security predicate. Multiple disabled security policies can target a single table, but only one can be enabled at any given time.  
  
## Remarks
The ALTER SECURITY POLICY statement is in a transaction's scope. If the transaction is rolled back, the statement is also rolled back.  
  
When using predicate functions with memory-optimized tables, security policies must include **SCHEMABINDING** and use the **WITH NATIVE_COMPILATION** compilation hint. The SCHEMABINDING argument can't be changed with the ALTER statement because it applies to all predicates. To change schema binding, you must drop and recreate the security policy.  
  
Block predicates are evaluated after the corresponding DML operation is executed. As such, a READ UNCOMMITTED query can see transient values that will be rolled back.  
  
## Permissions  
Requires the ALTER ANY SECURITY POLICY permission.  
  
Additionally the following permissions are required for each predicate that is added:  
  
-   SELECT and REFERENCES permissions on the function being used as a predicate.  
-   REFERENCES permission on the target table being bound to the policy.  
-   REFERENCES permission on every column from the target table used as arguments.  
  
## Examples  
The following examples demonstrate the use of the **ALTER SECURITY POLICY** syntax. For an example of a complete security policy scenario, see [Row-Level Security](../../relational-databases/security/row-level-security.md).  
  
### A. Adding an additional predicate to a policy  
The following syntax alters a security policy, adding a filter predicate on the `mytable` table.  
  
```sql  
ALTER SECURITY POLICY pol1   
    ADD FILTER PREDICATE schema_preds.SecPredicate(column1)   
    ON myschema.mytable;  
```  
  
### B. Enabling an existing policy  
The following example uses the ALTER syntax to enable a security policy.  
  
```sql  
ALTER SECURITY POLICY pol1 WITH ( STATE = ON );  
```  
  
### C. Adding and dropping multiple predicates  
The following syntax alters a security policy, adding filter predicates on the `mytable1` and `mytable3` tables, and removing the filter predicate on the `mytable2` table.  
  
```sql  
ALTER SECURITY POLICY pol1  
ADD FILTER PREDICATE schema_preds.SecPredicate1(column1)   
    ON myschema.mytable1,  
DROP FILTER PREDICATE   
    ON myschema.mytable2,  
ADD FILTER PREDICATE schema_preds.SecPredicate2(column2, 1)   
    ON myschema.mytable3;  
```  
  
### D. Changing the predicate on a table  
The following syntax changes the existing filter predicate on the mytable table to be the SecPredicate2 function.  
  
```sql  
ALTER SECURITY POLICY pol1  
    ALTER FILTER PREDICATE schema_preds.SecPredicate2(column1)  
        ON myschema.mytable;  
```  
  
### E. Changing a block predicate  
Changing the block predicate function for an operation on a table.  
  
```sql 
ALTER SECURITY POLICY rls.SecPol  
    ALTER BLOCK PREDICATE rls.tenantAccessPredicate_v2(TenantId) 
    ON dbo.Sales AFTER INSERT;  
```  
  
## See Also  
[Row-Level Security](../../relational-databases/security/row-level-security.md)   
[CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
[DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
[sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
[sys.security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
