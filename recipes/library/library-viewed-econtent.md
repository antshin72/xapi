# econtent viewed statement template

Based on generic template statement: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#econtent)

## Purpose
This template defines the structure and terms to record the experience of viewing econtent.

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The actor entity describes the individual that is viewing econtent.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "john-smith",
            "homePage": "http://ezproxy.jisc.ac.uk"
        }
    },
```

### Timestamp
An ISO 8601 format timestamp that corresponds to the time when the content was viewed.

### Example:

``` javascript
"timestamp": "2015-09-18T01:54:51.484Z",
`````` 

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb, [viewed](/vocabulary.md#verbs), denotes the action of the user's browser or app requesting the econtent.

### Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```


### Object
Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://onlinelibrary.jisc.ac.uk/doi/10.1111"   	 	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/resource"
		},
		"extensions": {
     		 "http://xapi.jisc.ac.uk/subType": "http://xapi.jisc.ac.uk/journal"
	 	}
    	}
}
```





### Context

### Example:

``` javascript
	"context": {
		"platform": "UxAPI",
		"extensions": {

			"http://xapi.jisc.ac.uk/version": "1.0.1",
			"http://xapi.jisc.ac.uk/sessionId": "A438L",
			"http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
			"https://xapi.jisc.ac.uk/statementCat": "Library"
		}
	}
```


## Full Example
``` javascript
{
	"version": "1.0.0",
	"actor": {
		"objectType": "Agent",
		"account": {
			"name": "Jsmith12",
			"homePage": "http://ezproxy.jisc.ac.uk"
		}
	},
	"timestamp": "2015-09-18T01:54:51.484Z",
	"verb": {
		"id": "http://id.tincanapi.com/verb/viewed",
		"display": {
			"en": "viewed"
		}
	},
	"object": {
		"objectType": "Activity",
		"id": "http://onlinelibrary.jisc.ac.uk/doi/10.1111",
		"definition": {
			"type": "http://id.tincanapi.com/activitytype/resource",
		}
	},	
	"context": {
		"platform": "UxAPI",
		"extensions": {
			"http://xapi.jisc.ac.uk/version": "1.1",
			"http://xapi.jisc.ac.uk/sessionId": "32456891",
			"http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
			"https://xapi.jisc.ac.uk/statementCat": "Library"
		}
	}
}
```
