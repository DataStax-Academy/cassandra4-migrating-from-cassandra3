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
<span class="step-count"> Step 3 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step4"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Verify that the node is ready to be upgraded</div>

In this step, we will verify that the Cassandra 3.x cluster is ready to be upgraded. There are nine factors to consider:

**Current State**
All nodes in the cluster need to be in the ‘Up and Normal’ state. Check that there are no nodes in the cluster that are in a state different to *Up and Normal*. 

✅ List any nodes **not** in the *UN* state:
```
nodetool status | grep -v UN
```

**Disk Space**
✅ Verify that each node has at least 50% diskspace free:
```
df -h
```

**Errors**
✅ Ensure that there are no unresolved errors (also, see warnings) in the log:
```
grep -e "WARN" -e "ERROR" cassandra3/logs/system.log
```

**Gossip Stable**
✅ Verify all entries in the gossip information output have the gossip state ‘STATUS:NORMAL’. Check if there are any nodes that have a status other than ‘NORMAL’:
```
nodetool gossipinfo | grep STATUS | grep -v NORMAL
```

**Dropped Messages**
✅ Establish that no Dropped Message log messages have been recorded on any node in the previous 72 hours.
```
nodetool tpstats | grep -A 12 Dropped
```

**Backups Disabled**
Verify that all automatic backups have been disabled. This includes disabling *Medusa* and any scripts that call `nodetool snapshot` until the upgrade is complete.

**Repair Disabled**
Verify that *repairs* have been disabled. This includes disabling automated repairs in *Reaper*.

**Monitoring**
Upgrading may result in a temporary reduction in performance, as it simulates a series of temporary node failures. Understanding how the upgrade impacts the performance of the system, both during and after, is crucial when working through the process. 

**Availability**
Confirm that areas of the application that require strong consistency are using the `LOCAL_QUORUM` consistency level and the replication factor of 3. When `LOCAL_QUORUM` is used with a replication factor below 3, all nodes must be available for requests to succeed. A rolling restart using this configuration will result in full or partial unavailability while a node is *DOWN*.

You are now ready to begin the upgrade.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
