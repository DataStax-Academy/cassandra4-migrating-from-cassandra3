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
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step5"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Enable audit logging in cassandra.yaml</div>

Previously, you enabled audit logging for a Cassandra node using `nodetool`, but the logging will not remain enabled when the node is restarted unless you edit the `cassandra.yaml` file. In this step, you will learn how to audit logging in `cassandra.yaml`. 

✅ Open the `cassandra.yaml` file in the editor:
```
nano $HOME/apache-cassandra/conf/cassandra.yaml
```

✅ Find the line that contains `audit_logging_options:` and change `enabled` from `false` to `true`. Your edited file may look like this:

<pre class="non-executable-code">
audit_logging_options:
    enabled: true
    logger:
      - class_name: BinAuditLogger
    # audit_logs_dir:
    # included_keyspaces:
    # excluded_keyspaces: system, system_schema, system_virtual_schema
    # included_categories:
    # excluded_categories:
    # included_users:
    # excluded_users:
    # roll_cycle: HOURLY
    # block: true
    # max_queue_weight: 268435456 # 256 MiB
    # max_log_size: 17179869184 # 16 GiB
    ## archive command is "/path/to/script.sh %path" where %path is replaced with the file being rolled:
    # archive_command:
    # max_archive_retries: 10
</pre>

For the new configuration settings in `cassandra.yaml` to take effect, you will need to save the file and restart Cassandra.

In this step, you learned how to enable audit logging in the `cassandra.yaml` file. 


<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

