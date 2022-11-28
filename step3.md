<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Migrating from Cassandra 3.x to 4.x</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 4</span>
 <a href='command:katapod.loadPage?[{"step":"step4"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Configure audit logging</div>

In this step, you will look at some of the configurable properties of audit logging. Then, you will demonstrate setting and unsetting one of these properties.

✅ Get the list of available audit logging properties:
```
nodetool help enableauditlog
```

All of these properties may be configured with `nodetool` or in `cassandra.yaml`. Properties configured with `nodetool` temporarily override settings in `cassandra.yaml`. However, properties configured with `nodetool` do not persist across shutdowns. Properties configured in `cassandra.yaml` persist across server shutdowns. 

In this example, you will use the `excluded-categories` property to exclude queries from the audit log. Here is the 
list of audit log categories:
- `QUERY`: `SELECT`
- `DML`: (Data Manipulation Language) `UPDATE`, `DELETE`, `INSERT`, `BATCH`
- `DDL`: (Data Definition Language) `TRUNCATE`, `CREATE_KEYSPACE`, `ALTER_KEYSPACE`, `DROP_KEYSPACE`, `CREATE_TABLE`, `DROP_TABLE`, `DROP_TRIGGER`, `CREATE_INDEX`, `DROP_INDEX`, `CREATE_TYPE`, `DROP_AGGREGATE`, `ALTER_VIEW`, `CREATE_VIEW`, `CREATE_FUNCTION`, `ALTER_TABLE`, `CREATE_AGGREGATE`, `DROP_VIEW`, `DROP_TYPE`, `DROP_FUNCTION`, `CREATE_TRIGGER`, `ALTER_TYPE`
- `DCL`: (Data Control Language) `LIST_USERS`, `GRANT`, `REVOKE`, `DROP_ROLE`, `ALTER ROLE`, `LIST_ROLES`, `LIST_PERMISSIONS`, `CREATE_ROLE`
- `OTHER`: `USE_KEYSPACE`
- `AUTH`: `LOGIN_ERROR`, `UNAUTHORIZED_ATTEMPT`, `LOGIN_SUCCESS`
- `ERROR`: `REQUEST_FAILURE`
- `PREPARE`: `PREPARE_STATEMENT`


✅ Execute and log a query:
```
nodetool enableauditlog

cqlsh -k ks_audit_logging \
      -e "SELECT * FROM songs WHERE artist = 'Elton John';"
```

✅ Execute and do not log a query:
```
nodetool enableauditlog --excluded-categories QUERY

cqlsh -k ks_audit_logging \
      -e "SELECT * FROM songs WHERE artist = 'Paul Simon';"
```

✅ Display the audit log:
```
auditlogviewer $HOME/apache-cassandra/logs/audit/
```

You should see the query for Elton John songs but not the query for Paul Simon songs.

In this step, you explored the configurable properties of audit logging. Next, you used `nodetool` to exclude logging queries. Then, you performed queries and used `auditlogviewer` to verify how they were logged.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
