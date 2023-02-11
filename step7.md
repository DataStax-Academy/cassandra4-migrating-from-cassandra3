<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Migrating from Cassandra 3.x to 4.x</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span> 
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"finish"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Verify that the node has been successfully migrated</div>

In this step, you will verify that the Cassandra node has been upgraded and that the data is still available.

✅ Verify that the Cassandra version is 4.x:
```
nodetool version
```

✅ Verify that the node is in the *UP* and *NORMAL* (*UN*) state:
```
nodetool status
```

✅ Verify that there are no errors:
```
grep -e "WARN" -e "ERROR" cassandra4/logs/system.log
```

✅ Start the CQL shell:
```
cqlsh
```

✅ Use the keyspace:
```
USE united_states;
```

✅ Verify that the data is accessible:
```
SELECT * FROM cities_by_state;
```

If you can see the data, you have successfullly upgraded from Cassandra 3.x to 4.x!

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

