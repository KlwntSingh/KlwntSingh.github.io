---
title: Class Diagrams
layout: post
---
      

# undo-linux  

## Command   

* execute   

* unexecute   

* wraps util   

* new object for every util with different concrete implementation of util   

## util   

* name   

* options   

* args   

* undo: util   

* subclasses will be created for every util   

## Controller   

### parse   

* parses string command and creates command util object   

### undo   

* class unexecute on command   

## state of mind   

* reading command pattern   

# fs-advanced  

## action   

* name   

* options   

* args   

* perform   

* subclass for every different action   

## option   

* action   

* inline: boolean   

* subclas for every possible option   

## controller   

### parse   

* creates new action object with args and options   

* execute   

## state of mind   

* reading command pattern   

# factory method  

## Pizza   

* NYStyleCheesePizza   

* NYStyleVegPizza   

* CaliforniaCheesePizza   

* CaliforniaVegPizza   

## PizzaStore   

### NYStylePizzaStore   

* if conditions for veg, cheese pizza   

### CaliforniaStylePizzaStore   

* if condition for veg, cheese pizza   

## abstract factory   

### Pizza   

* CheesePiza   

* VegPizza   

* uses PizzaIngredient   

### PizzaIngredient   

* NYStyleIngredient   

* CaliforniaIngredients   

### PizzaStore   

#### NYStylePizzaStore   

* if conditions for veg, cheese pizza   

#### CaliforniaStylePizzaStore   

* if condition for veg, cheese pizza   

# Sheet 4  

## Vehicle   

* drive   

## ParkingLot   

* park   

* moveIn   

* moveOut   

* availabletime   

* alotParkingSpace   

* payForParkingSpace   

* Payment   
