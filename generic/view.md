# resource_viewed generic Statement template

## Purpose
This generic Statement template describes the structure and terms to record the experience of viewing a resource on a platform. Use this template to create a specific viewing Statement template, for example for a student viewing stats in a student app.

The entities and properties described here represent a typical Statement template. Further properties or constraints could be defined to create a login Statement template for a more specific purpose.

Natural language example of a typical view Statement: "John Smith viewed a module in his university Moodle VLE."

Examples:

- [VLE resource viewed](../recipes/vle/Module-View.md)
- [Mobile app content viewed](../recipes/studyapps/mobile-app.md)
- [Blackboard course viewed ](../recipes/blackboard/course_access.json)
- [Moodle module viewed ](../recipes/moodle/moduleview.js)

### Actor
The Actor entity is used to identify the individual that is viewing the resource. It uses the Jisc Profile common entity [ActorA](/common_structures.md#actora).

#### Entity properties:

<table>
<tr><th>Property</th><th>Description</th></tr>
<tr>
<td>actor.objectType [1]</td><td>Must have the value "Agent". Actors of type "Group" are not supported in the Jisc Profile.</td>
</tr>
<tr>
<td>actor.name [0..1]</td><td>Full name of user.</td>
</tr>
<tr>
<td>	
actor.account [1] <br/>
actor.account.name [1] <br/>
actor.account.homepage [1] <br/>
</td>
<td>A JSON Object with <b>account.name</b> giving a system login id for the subject of the Statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td></tr>
</table>

### Example:

``` Javascript
"actor": {
  "objectType": "Agent",
  "name": "John Smith",
  "account": {
    "name": "jsmith12",
    "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
  }
}
```

### Verb
The Verb used in view Statements is [viewed](../vocabulary.md#verbs). It denotes the action of the user requesting the resource that the user wishes to view. It uses the Jisc Profile common entity [VerbA](../common_structures.md#verba). 

#### Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. http://id.tincanapi.com/verb/viewed in viewed statements.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. "viewed" in viewed statements </td>
	</tr>
</table>



### Example:

``` javascript
"verb": {
  "id": "http://id.tincanapi.com/verb/viewed",
  "display": {
    "en" : "viewed"
  }
}
```

### Object

The Object for viewed Statements identifies what is being viewed. It uses the Jisc Profile common entity [ObjectA](../common_structures.md#objecta).


#### Object Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the Object of the Statement. This must be unique (within a given platform) across all Object types.</td>
	</tr>
		<tr>
		<td>object.definition.type [1]<br />
	object.definition.name [0..1]<br />
	object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]<br />
	object.definition.extensions.http://xapi.jisc.ac.uk/uddModInstanceID [0..1]</td>
		<td>A JSON Object comprising both standard xAPI attributes and the Jisc Profile 'subType' and 'uddModInstanceID' extensions.<br/>
    The <b>type</b> indicates the type of the Object of the Statement. It is required and valid values are listed on the <a href="vocabulary.md#31-activity-types">vocabulary page</a>.<br/>
    The <b>name</b> is optional.<br/>
    The <b>subType</b> extension may be used to indicate the sub-type of this Activity, if applicable for the recipe being used to create the Statement. This qualifies the object.objectType, and is described on the <a href="vocabulary.md#32-object-definition-extensions">vocabularies page</a>.<br />
  </tr>
	
</table>

### Example

``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://courses.alpha.jisc.ac.uk/moodle",
  "definition": {
    "type": "http://activitystrea.ms/schema/1.0/application",
    "name": {
      "en": "University of Jisc VLE"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
    }
  }
}

```

### Context
The Context entity can be used to describe any surrounding circumstances, including for example the device used and id of the module. If the device supports it, session Ids and ip-addresses can be recorded. Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page. 

#### Entity properties:
<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr><td>context.platform [1]</td>
	<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard".</td></tr>
	<tr><td>context.extensions.version [0..1]
		 context.extension.sessionId [0..1]
		 context.extension.ip-address [1]
		 context.extension.courseArea [0..1]
		 </td>
		<td>Four extensions are provided, with IRIs as defined on the <a href="vocabulary.md#41-context-extensions">vocabularies page</a>.
  	  The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI Profile found on the ReadMe page. <br/>
	The <b>courseArea</b> identifies umbrella course/parent area by its UDD Module Instance ID or VLE Module ID. More information can be found on the <a href="vocabulary.md#umbrella-course-area">vocabularies page</a>.
		</td></tr></table>

### Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	
      	"http://xapi.jisc.ac.uk/courseArea": {
				"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
			},
					
	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
	"http://xapi.jisc.ac.uk/version" : "1.0.2"
			}
        }
```

