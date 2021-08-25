---
tags: engineering, diagram
---

### What
A graphical resprentation of steps. These steps are made in sequential order that is used to visualize a process, from starting point to end point. 

During the process, some steps are considered as condition value with yes/no result, which leads to different use cases. 

A `happy case` in flow chart describes a successful process from starting point to ending point, when the user goes through steps with `yes` value and reach the desired result. 

### When
Process, workflow and operation instructions for different uses cases.

### Example
Hotel booking Flow
1. Reservation
2. Check for Availability
	1. yes - make reservation
	2. no - ask for awaiting
3. Make reservation
4. Confirm booking -> Payment
	1. yes - checkin
	2. no - cancel
5. Check in 
6. Checkout
7. Payment
8. Renewal 
	1. yes - ask for awaiting