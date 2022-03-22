# 288_tepmlate

#EX288 - Template Question 

create the project indy 
   oc new-project indy
   wget <url for the yaml file only .. not the json file >
   vi <the yaml file>

4 Changes 
     -> Name Of the Template
     -> labels
     -> Namespace 
     -> Git URL 
        -> Go to the parameter Section
            -> search for the /SOURCE_REPOSITORY_URL or GIT_REPO and change the URL to Correct value 
			
2 Changes
     -> Get the Image Version
        -> oc get is -n openshift | grep php ** in exam cluster it will be 8.0 **
        -> oc get is -n openshift | grep mysql ** in exam cluster it will be 8.0 **      	 
     -> search for 
         /php:    # in exam there will be php: 5.7 and you have to replace it with the version you got from the above command eg 8.0  
         /mysql:  # have to replace it with the version you got from the above command eg 8.0
		

USE CASES :
CASE I 
     -> search for 
	    -> APPLICATION_DOMAIN 
           -> make value : empty list " " ## remove the line and just keep " " there 
           -> required: true              ## add this line 
--------------------------------------------------------------------------------------
#### Delete all components #### the command to delete it will be givin in exam ####
--------------------------------------------------------------------------------------		   
CASE II		  

     -> search for 
	    -> HELLO_MESSAGE              ## it will be available in 2 locations .. one in env and one parameter 
		
     # In parameter section 
	 
	  -name: HELLO_MESSAGE            ## already in template 
          value: Bonjour                  ## Fix with proper Name 
		 
	  -name: HELLO_AUDIENCE           ## add it in template the below HELLO_MESSAGE 
          value: Engineer 

CASE III

     -> search for 
	    -> HELLO_MESSAGE  ## it will be available in 2 locations .. one in env and one parameter 

     # In environment section 
	 
	  -name: HELLO_MESSAGE           ## already in template 
          value: ${HELLO_MESSAGE}        ## already in template 
		 
	  -name: HELLO_AUDIENCE          ## add it in template the below HELLO_MESSAGE 
          value: ${HELLO_AUDIENCE}       ## add it in template 

oc create -f test.yml
open in browser the URL (check the route) it will show u Bjourn Engineer , ignore the data base 

oc new-app 
oc new-app 
oc new-app 
