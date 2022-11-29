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
<span class="step-count"> Step 2 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Create a keyspace and table, and insert data</div>

In this step, you will create a keyspace and table, and populate them with some data.

✅ Start the CQL shell:
```
cqlsh
```

✅ Create the keyspace:
```
CREATE KEYSPACE united_states 
WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};

USE united_states;
```

✅ Create the table:
```
CREATE TABLE cities_by_state (
    state text,
    name text,
    population int,
    PRIMARY KEY ((state), name)
);
```

✅ Insert the top 10 largest U.S. cities by population:
```
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('New York','New York City',8622357);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('California','Los Angeles',4085014);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Illinois','Chicago',2670406);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Texas','Houston',2378146);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Arizona','Phoenix',1743469);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Pennsylvania','Philadelphia',1590402);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Texas','San Antonio',1579504);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('California','San Diego',1469490);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('Texas','Dallas',1400337);
INSERT INTO cities_by_state (state, name, population) 
  VALUES ('California','San Jose',1036242);
```

✅ Verify that the data has been loaded:
```
SELECT * FROM cities_by_state;
```

✅ Retrieve all the cities in California:
```
SELECT * FROM cities_by_state WHERE state = 'California';
```

✅ Exit the CQL shell and clear the screen:
```
exit
clear
```

You have loaded the data, continue to the next step.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
