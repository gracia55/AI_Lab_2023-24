# Ex.No: 12  Planning –  Monkey Banana Problem
### DATE: 14.03.2024                                                                           
### REGISTER NUMBER : 212222060295
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 

### Program:
```
(define (domain monkey)	       
  (:requirements :strips)
   (:constants monkey box knife bananas glass waterfountain)
   (:predicates (location ?x)
	       (on-floor)
	       (at ?m ?x)
	       (hasknife)
	       (onbox ?x)
	       (hasbananas)
	       (hasglass)
	       (haswater))
   ;; movement and climbing
  (:action GO-TO
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
	     :effect (and (at monkey ?x) (not (at monkey ?y))))
   (:action CLIMB
	     :parameters (?x)
	     :precondition (and (location ?x) (at box ?x) (at monkey ?x))
	     :effect (and (onbox ?x) (not (on-floor))))
   (:action PUSH-BOX
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) 
				 (on-floor))
	     :effect (and (at monkey ?x) (not (at monkey ?y))
			   (at box ?x)    (not (at box ?y))))
  ;; getting bananas
  (:action GET-KNIFE
	     :parameters (?y)
         :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
	     :effect (and (hasknife) (not (at knife ?y))))
  (:action GRAB-BANANAS
	     :parameters (?y)
	     :precondition (and (location ?y) (hasknife) 
                                 (at bananas ?y) (onbox ?y))
	     :effect (hasbananas))
  ;; getting water
  (:action PICKGLASS
	     :parameters (?y)
	     :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
	     :effect (and (hasglass) (not (at glass ?y))))
  (:action GETWATER
	     :parameters (?y)
	     :precondition (and (location ?y) (hasglass)
				 (at waterfountain ?y)
				 (at monkey ?y)
				 (onbox ?y))
	     :effect (haswater)))
```

### Input :
```
(define (problem pb1)
    	(:domain monkey)
  	(:objects p1 p2 p3 p4 bananas monkey box knife)
  	(:init (location p1)
		(location p2)
		(location p3)
		(location p4)
	 	(at monkey p1)
		(on-floor)
		(at box p2)
		(at bananas p3)
	 	(at knife p4)
	)
  	(:goal (and (hasbananas)))
)
```

### Output/Plan:
![326326538-f7a3bbb5-0d9b-43c1-bf38-9e1171e142af](https://github.com/user-attachments/assets/1f702def-bfda-4975-803d-a9ed80d6a565)


![326326586-40b25c93-136c-410d-9b89-95ee5000b995](https://github.com/user-attachments/assets/d461030b-b854-4fd6-b669-adb6435b7be2)

![326326615-5867317a-726e-4940-b219-23c9edcaebf0](https://github.com/user-attachments/assets/3f8a6ee8-ac12-45d2-8e4e-d2784cb37ed7)


![326326680-cb8a826d-b025-4dc0-8348-12ea863ef04d](https://github.com/user-attachments/assets/a879c7f8-5b16-492a-92b1-c3ab70f529ee)

![326326715-9842351f-7a74-4c32-8523-0db328bcf00c](https://github.com/user-attachments/assets/c052553b-6012-4f9b-b7b1-5626634ce9bc)


![326326757-cd4fe5d4-bbfc-4f4a-be73-2517abc10869](https://github.com/user-attachments/assets/da5d7092-f7d9-4d4d-a669-f9c795ee384c)





### Result:
Thus the plan was found for the initial and goal state of given problem.
