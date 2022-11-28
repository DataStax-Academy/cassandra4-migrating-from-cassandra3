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
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 4</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Enable audit logging via nodetool</div>

In this step, you will use `nodetool` to dynamically enable and disable audit logging. Next, you will insert and update some data. Finally, you will view the audit log.

✅ Use `nodetool` to enable audit logging:
```
nodetool enableauditlog
```

✅ Start the CQL shell:
```
cqlsh -k ks_audit_logging
```

✅ Insert a row into the `songs` table:
```
INSERT INTO songs (artist, title, year) VALUES ('Elton John', 'Daniel', 1974);
```

✅ Wait a minute! Elton John released *Daniel* in 1973 on the album *Don't Shoot Me I'm Only The Piano Player*!
Update the row to reflect the correct year:
```
UPDATE songs SET year = 1973 WHERE artist = 'Elton John' AND title = 'Daniel';
```

✅ Make sure the update worked:
```
SELECT * FROM songs WHERE artist = 'Elton John' AND title = 'Daniel';
```

You should see *Daniel* with the correct year - 1973.

✅ Exit the CQL shell:
```
exit
```

✅ The audit log is stored in binary format so you will use `auditlogviewer` to see it in *human-readable* form:
```
auditlogviewer $HOME/apache-cassandra/logs/audit/
```

Ignore any Java warnings you may see. The log output should contain the `INSERT`, `UPDATE` and `SELECT` commands you entered along with a timestamp, username and more.

Audit logs will often contain sensitive data (account numbers, employee names, etc.). Therefore, the files (and the directories that contain them) should be protected using the host operating system's file system protections. Since the default audit logger implementaion does not give the option to redact specific fields, sensitive data should be masked or removed before sharing.

✅ Use `nodetool` to disable audit logging:
```
nodetool disableauditlog
```

✅ Start the CQL shell:
```
cqlsh -k ks_audit_logging
```

✅ Insert two more songs into the `songs` table:
```
INSERT INTO songs (artist, title, year) VALUES ('Elton John', 'Bennie and the Jets', 1973);
INSERT INTO songs (artist, title, year) VALUES ('Steve Miller Band', 'The Joker', 1974);
```

✅ Exit the CQL shell:
```
exit
```

✅ Take another look at the audit log:
```
auditlogviewer $HOME/apache-cassandra/logs/audit/
```

Since we disabled audit logging, the most recent inserts are not reflected in the logs.

In this step, you used `nodetool` to enable and disable logging. You also used `auditlogviewer` to view the audit logs.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
