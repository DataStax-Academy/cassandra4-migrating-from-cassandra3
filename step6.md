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
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 6 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step7"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Start Cassandra 4.x</div>

In this step, you will configure `cassandra.yaml` and start Cassandra 4.x.

✅ Change the number of virtual nodes to 256 since the 3.x node had 256 and the 4.x node is set to 16 by default. Set `num_tokens` to 256 in Cassandra 4.x:
```
sed -i 's/num_tokens: 16/num_tokens: 256/' cassandra4/conf/cassandra.yaml
```

✅ Point the Cassandra 4.x node to the Cassandra 3.x node data files:
```
sed -i 's|# data_file_directories:|data_file_directories:|' cassandra4/conf/cassandra.yaml
sed -i "s|#     - /var/lib/cassandra/data|    - $GITPOD_REPO_ROOT/cassandra3/data/data|" cassandra4/conf/cassandra.yaml
```

✅ Start the Cassandra 4.x node:
```
cassandra
```

Look for the `state jump to NORMAL` message to indicate that the node is running.

✅ Clear the screen and continue:
```
clear
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step5"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step7"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

