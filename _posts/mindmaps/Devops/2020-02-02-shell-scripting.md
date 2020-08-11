---
title: shell scripting
layout: post
---
    
# Shell Scripting

## positional arguments 
* same positional arguments works for functions and scripts 
* #### $1, $2...$9 
	* $1 - first argument 
	* $0 - shell script name 
* #### $a 
	* all the positional parameters 

## secondary prompt 

## command substitution 
* $(COMMAND) 

## executing more than 1 command together 
* #### ; 
	* commands executed independent of previous command 
* #### && 
	* when first success, second is executed 

## cronjob 
* total 6 args 
* #### 1st arg 
	* minutes 
* #### 2nd 
	* hours 
* #### 3rd 
	* days in month 
* #### 4th 
	* month 
* #### 5th 
	* days in week 
* #### 6th 
	* command to execute 
* #### * 
	* means every instance 
* #### / 
	* defines step 
	* eg: /2 
		* means every 2 hours or minutes etc 
* Subtopic 10 

## control instructions 
* #### conditional 
	* if 
		* then 
		* fi 
		* elif 
		* else 
* #### case control 
	* switch 
		* case 
		* ;; 
* #### loop 
	* for 
		* in 
		* do 
		* done 
	* while 
	* untill 

## vi 
* command mode 
* insertion mode 

## standard input vs command line argument 
* shell scripts should be programmed to take input from both standard input and command line argument 
* #### standard input - basically the actual content on which script will do processing. 
	* it comes in picture when pipe in commands is used.the standard input is not passed line by line but as a whole 
	* xargs is another utility which enables standard input to taken as command line argument 
* command line argument means actually passing file to script from which content will be read and processed on 

---
