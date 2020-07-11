---
title: Microservices
layout: post
---
      

# Microservices  

## scale cube   

### x-axis   

* running clone of services   

### y-axis   

#### splitting the service into multiple services and than scaling these services   

* based on verb   

* based on noun   

### z-axis   

* clonning the service and each server is only responsible for only subset of data   

## each microservice has it's own database and consistency between database of different service can be by two patterns   

### SAGA pattern   

#### local transaction triggers event to tell next microservice to trigger their local transaction   

##### two ways   

###### choreography   

* asynchronous message passing   

###### orchestration   

* syncrhonous message passing   

### 2pc   

#### two phase commit   

* transaction cordinator decide whether to commit or rollback   
