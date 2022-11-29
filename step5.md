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
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 5 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step6"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Install Cassandra 4.x</div>

In this step, you will dowanload and unpack the Cassandra 4.0.0 distribution.


✅ Download and install Cassandra 4.x:
```
wget https://archive.apache.org/dist/cassandra/4.0.5/apache-cassandra-4.0.5-bin.tar.gz

tar -xzf apache-cassandra-4.0.5-bin.tar.gz

rm apache-cassandra-4.0.5-bin.tar.gz

mv apache-cassandra-4.0.5 cassandra4
```


Update the PATH variable.
```
export PATH="/usr/bin:/usr/share/cassandra4/bin:/usr/share/cassandra4/tools/bin:$PATH"
```

Clear the screen and continue.
```
clear
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step4"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step6"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

