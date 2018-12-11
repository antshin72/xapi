# vle_assignment_submitted Statement template

[Statement Template Changes](/version_changes.md#assignment-submitted)

## Purpose
This Statement template records a user submitting an assignment.

## Definition

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The Actor entity describes the individual who has submitted the assignment.

``` Javascript
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "jsmith12",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb [completed](/vocabulary.md#verbs) describes the action of completing an Activity - finishing it in its entirety.

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en": "completed"
        }
    },
``` 

### Object
Common entity identifier: ObjectB, as defined on the [common structures](/common_structures.md#objectb) page.

Example:

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/assessment",
			"name":{
				"en":"xapi Assignment"
			},
		  	  "extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
			
		}
```

### Context
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page.

Example:

``` javascript
"context": {
	        
        "platform": "Moodle",

        "extensions": {
		
      		"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0"
				},
			
			"http://xapi.jisc.ac.uk/statementCat": "VLE",
			"http://xapi.jisc.ac.uk/sessionId":"32456891",
         	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/version" : "1.1"
			"http://xapi.jisc.ac.uk/sequenceNumber" : 1

			}
		}
```

### Complete VLE Specific Examples
[Blackboard Assignment Submitted Example](/vle/blackboard/assignment_submitted.json)

[Moodle Assignment Submitted Example](/vle/moodle/assignment_submitted.json)
