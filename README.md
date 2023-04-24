# Laravel DDD Architecture Folders
## Ideal esqueleton from DDD architecture within Laravel world
  
### Table of Contents
1. [Description](#1-description)
2. [Architecture Folders](#2-architecture-folders)
3. [Details](#3-details)
4. [Just do it](#4-just-do-it)
  
#### 1. Description
This is a easy structure to work within Laravel, in order to DDD architecture. 
Of course, maybe could be better. Tell me if you think so.
In this case, I tried do not make strong changes on default Laravel's folder structure, to not need to make changes on his code.  
It's so simple like use separated modules perform by Nicolas Widart, and a few adds on the Laravel folders.  
( <a href="https://docs.laravelmodules.com">nWidart Modules</a> and his <a href="https://github.com/nWidart/laravel-modules">github place</a> ).  
In the future, each module should have 3 first folders, for infrastructure, application, and domain. By now, only the folder "models" has them.
  

#### 2. Architecture Folders
```
Source					 		
	app						
	bootstrap						
	config						
	database	(only general purpose. Define storage method)
	library		(our functions)				
	public						
	resources	(only general purpose)				
	routes		(only general purpose)				
	storage						
	test		(only general purpose)				
	vendor		(composer dependencies)				
	modules	
		module X					
			PublicConnector.php (all requirements needed for outside. This is all external modules can see)
			config				
			database        (extends from defined in Source database folder)
			http				
				back			
					controllers		
					middlewares		
					requests		
				front			
					controllers		
					middlewares		
					requests		
			models				
				application
					usecases
				domain
					DB      	(tables, extends from abstract layer)	
					Exceptions
					ValueObjects
					Contracts	(interfaces)
				infrastructure
			providers				
			resources				
				views			
					back    (admin users)
					front   (final users)
					emails  (templates)
				json			
			routes			(different access channels to the module) 				
				api			
				command			
				web			
			tests				
				feature			
					integration   (using other components and libraries)
					acceptation   (from whole http request)
				unit            (individual test)
							
		shared module 					
			contains everything shared between modules				
			Has a separate laywer for external libraries, that is used by project modules.				

```  
  
  
#### 3. Details
##### PublicConnector.php 
This is the first door to get everything in a module and should be the only one.  
It has the same name on each module.  
It's goal is provide simple access to all external requirements.  
Sometimes, after a while, maybe you will not remember all the abilities of the module, or how you should invoke a certain feature. Here, other modules would find all features of this module.


#### 4. Just do it
1. Install Laravel.
2. Install modules structure.
3. Add others folders.

## License
MIT




