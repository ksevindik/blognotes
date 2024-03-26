In our current project, we make use of the Hibernate Interceptor to perform auditing and track operations performed with our domain objects. 
Initially, we simply followed the instructions in the Hibernate In Action book. Basically, the steps are as follows:

1. Declare an Auditable interface and define methods within it for the information you want to audit about your domain objects. 
Our domain objects should implement this interface if they are to be auditable.
3. Define an AuditLog class to represent audit log information about our create/update/delete operations.
4. Implement an AuditLogInterceptor to capture insert, update, and delete events performed with our auditable domain objects, 
using the onSave, onFlushDirty, and onDelete callback methods respectively.
5. Finally, create and insert AuditLog objects for each inserted, updated, and deleted domain object.
   
It is important not to use the original Hibernate session object in your Interceptor, as it is illegal to do so in the callback methods of the Interceptor.
Therefore, we need to employ a new session to insert those AuditLog objects into our database.

So far, we have created an audit logging mechanism based on the above instructions, and it seemed to be working properly until we noticed that audit logs 
exist for operations that were involved in a rolled-back transaction. The original modified domain object is not in the database as it is rolled back, 
but its audit log exists in the log table! The reason for this is that, if you look at the code sample below for the AuditLogInterceptor, manipulated 
auditable domain objects are kept in three sets. On a postFlush method call, which occurs during transaction commit, we create and insert audit log records 
according to the contents of those sets, and finally, we clear the contents of those sets for a new turn. Unfortunately, postFlush is never called if a 
rollback occurs, hence the contents of the sets are not cleared. We resolved this situation by extending the HibernateTransactionManager and overriding its 
doRollback method, and clearing those contents by explicitly calling the reset method.

