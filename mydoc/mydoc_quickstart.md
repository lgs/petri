---
title: Quickstart
keywords: questions, quickstart, installation, server, integration
last_updated: March 31, 2016
sidebar: mydoc_quickstart
permalink: /mydoc_quickstart/
---

## Step 1 : Running Petri Server

There are two options:

- Use our runnable jar
- Install a Petri server from scratch

### Download our runnable jar

Download the [runnable-petri-server](https://github.com/wix/petri/releases/download/1.0/runnable-petri-server.jar)

run the server:
```bash
  java -jar runnable-petri-server.jar
```

### Install Petri Server

Prerequisite: Installing the Petri DB:
Petri requires a database. It has been tested against MySql and h2. 

* To create the schema, run the following:

```
CREATE TABLE experiments (id INT AUTO_INCREMENT, experiment MEDIUMTEXT, last_update_date BIGINT, orig_id INT, start_date BIGINT DEFAULT 0, end_date BIGINT DEFAULT 4102444800000, PRIMARY KEY(id, last_update_date))
CREATE TABLE specs (id INT PRIMARY KEY AUTO_INCREMENT, fqn VARCHAR (255) NOT NULL, spec MEDIUMTEXT, UNIQUE KEY (fqn))
CREATE TABLE metricsReport (server_name VARCHAR (255) NOT NULL, experiment_id INT NOT NULL, experiment_value VARCHAR (255) NOT NULL, total_count BIGINT,  five_minutes_count BIGINT , last_update_date BIGINT,  PRIMARY KEY (server_name, experiment_id, experiment_value))
CREATE TABLE userState (user_id VARCHAR (50) NOT NULL, state VARCHAR (4096) , date_updated BIGINT NOT NULL, PRIMARY KEY(user_id))
```
        
#### Installing a Petri server is easy

* compile the project  

* copy the resulting jar and lib folder from the target folder to your folder of choice.

```
cp petri-server/target/petri-server-1.19.0-SNAPSHOT.jar
cp -r petri-server/target/lib .
```
  
* create a 'petri.properties' file (values should match your db  and the port the server will receive RPC calls on )


```
db.username : <username_string>
db.password : <password_string>
db.url : <url_string>
server.port : <int>
```

* Run the server : `java -jar petri-server-1.19.0-SNAPSHOT.jar`



## Step 2 : [Creating a Petri BackOffice app]({{site.data.urls.mydoc_creating_a_petri_backoffice_app.url}}}) 

or, alternatively, [just issue a few http requests](https://github.com/wix/petri/wiki/Creating-&-Updating-Experiments-&-Specs)


## Step 3 : [Integrating Petri into your app](https://github.com/wix/petri/wiki/Integrating-Petri-into-your-app) 

or, alternatively, [Use Laboratory as a Service]({{site.data.urls.mydoc_using_laboratory_as_a_service.url}})