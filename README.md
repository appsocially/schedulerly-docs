# AppSocially Scheduler
This is the spec for the AppSocially Scheduler service.

## Version: 1.0.1

### Terms of service
http://

**Contact information:**  
hello@appsocial.ly  

**License:** [](http://)

[Find out more about AppSocially Scheduler](http://)
### Security
**schedulerAuth**  

|oauth2|*OAuth 2.0*|
|---|---|
|Authorization URL|http://|
|Flow|implicit|
|**Scopes**||
|write:users|modify users|
|read:users|read users|

**apiKey**  

|apiKey|*API Key*|
|---|---|
|Name|apiKey|
|In|header|

### /users

#### POST
##### Summary:

Create a user

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | User object to create | Yes | [UserIn](#userin) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | User created | object |
| 400 | Invalid input |  |

##### Security

| Security Schema | Scopes | |
| --- | --- | --- |
| schedulerAuth | write:users | read:users |

#### GET
##### Summary:

Get all users

##### Description:



##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of users | [ [UserOut](#userout) ] |

### /users/{userId}

#### GET
##### Summary:

Get user with Id

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | User | [UserOut](#userout) |
| 400 | Invalid Id |  |
| 404 | User not found |  |

#### DELETE
##### Summary:

Delete user with Id

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path |  | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Delete successful |
| 400 | Invalid Id |
| 404 | User not found |

### /users/{userId}/slots

#### GET
##### Summary:

Get user slots with user Id

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Fetch all slot for specified user | [ [UserSlotOut](#userslotout) ] |
| 400 | Invalid Id |  |

### /users/{userId}/slot

#### POST
##### Summary:

Create slot and assign to user

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path |  | Yes | string |
| body | body | Create slot for user | Yes | [UserSlotIn](#userslotin) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Create slot for specified user | [ [UserSlotOut](#userslotout) ] |

### /users/{userId}/rules

#### GET
##### Summary:

Get rules for users

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [UserRule](#userrule) |

#### POST
##### Summary:

Set rules for users

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |
| body | body | Create or update user rule set | Yes | [UserRule](#userrule) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [UserRule](#userrule) |

### /users/{userId}/rules/timeslots

#### GET
##### Summary:

Fetch a list of timeslots generated from user rules

##### Description:

Currently this will generate timeslots within the next seven days

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |
| duration | query | duration of meeting in minutes | Yes | string |
| days | query | number of days to generate | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Fetch all slot for specified user | [ [EmptySlot](#emptyslot) ] |

### /users/{userId}/meetings

#### GET
##### Summary:

Fetch a list of user meetings

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [ [Meeting](#meeting) ] |

### /users/{userId}/contacts

#### GET
##### Summary:

Fetch a list of contacts relevant to user

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [ [Attendee](#attendee) ] |

### /users/{userId}/event/upcomming

#### GET
##### Summary:

Fetch a list of events from integrated calendars

##### Description:

Currently this will fetch all events three months in advance

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [ [Event](#event) ] |

### /users/{userId}/rules/exclude-start-times

#### PUT
##### Summary:

Add timeslots to ignore when generating slots from rules

##### Description:

When generating slots automatically start times that had been specified will be ignored

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |
| body | body | Meeting object to create | Yes | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of start times passed through | [ string ] |

### /users/{userId}/calendars

#### GET
##### Summary:

Get a list of calendars the user is assigned to

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| userId | path | Id of user | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of start times passed through | [ object ] |

### /meetings

#### POST
##### Summary:

Create a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Meeting object to create | Yes | [Meeting](#meeting) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Meeting | [Meeting](#meeting) |

#### GET
##### Summary:

Get all meetings

##### Description:



##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of meetings | [ [MeetingOut](#meetingout) ] |

### /meetings/{meetingId}

#### GET
##### Summary:

Get a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Meeting | [Meeting](#meeting) |
| 400 | Invalid Id |  |
| 404 | Meeting not found |  |

#### PUT
##### Summary:

Update a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |
| body | body | Meeting object update | Yes | [Meeting](#meeting) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Meeting | [Meeting](#meeting) |
| 400 | Invalid Id |  |
| 404 | Meeting not found |  |

#### DELETE
##### Summary:

Delete a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Deleted meeting | object |
| 400 | Invalid Id |  |
| 404 | Meeting not found |  |

### /meetings/{meetingId}/slots

#### GET
##### Summary:

Get all slots of a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of slots of a particular meeting | [ [SlotOut](#slotout) ] |
| 400 | Invalid Id |  |
| 404 | Meeting not found |  |

#### PUT
##### Summary:

Add a slot to a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |
| body | body | Slot object to add | Yes | [SlotIn](#slotin) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Added slot | [SlotOut](#slotout) |
| 400 | Invalid Id |  |
| 404 | Meeting not found |  |

### /meetings/{meetingId}/slots/{slotId}

#### GET
##### Summary:

Get a slot of a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |
| slotId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | A slot of a particular meeting | [SlotOut](#slotout) |
| 400 | Invalid Id |  |
| 404 | Meeting or slot not found |  |

#### PUT
##### Summary:

Update a slot of a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |
| slotId | path |  | Yes | string |
| body | body | Slot object to update | Yes | [SlotUpdate](#slotupdate) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | The updated slot | [SlotOut](#slotout) |
| 400 | Invalid Id |  |
| 404 | Slot not found |  |

#### DELETE
##### Summary:

Delete a slot of a meeting

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |
| slotId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Deleted slot of a particular meeting | object |
| 400 | Invalid Id |  |
| 404 | Meeting or slot not found |  |

### /meetings/{meetingId}/attendees

#### GET
##### Summary:

Fetch list of attendees from meeting id

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| meetingId | path |  | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [ [UserOut](#userout) ] |

### /slots

#### POST
##### Summary:

Create new slot

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body |  | No | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of open timeslots | [ [Event](#event) ] |

### /slots/omakase

#### POST
##### Summary:

Get open slots based on attendee calendar events

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body |  | No | [OmakaseIn](#omakasein) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of open timeslots | [ [Event](#event) ] |

### /slots/{slotId}

#### PATCH
##### Summary:

Update slot

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| slotId | path |  | Yes | string |
| body | body | Slot object | No | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of open timeslots | [ [Event](#event) ] |

### /slots/{slotId}/attendee

#### POST
##### Summary:

Add attendee to slot

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| slotId | path |  | Yes | string |
| body | body | Slot object | No | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of open timeslots | [ [Attendee](#attendee) ] |

### /slots/{slotId}/attendee/{attendeeId}

#### DELETE
##### Summary:

Delete attendee from slot

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| slotId | path |  | Yes | string |
| attendeeId | path | Attendee's Id | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Empty Result | object |

### /slots/move-attendee

#### PUT
##### Summary:

Move attendee to slot

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body | Move objectt | No | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List of open timeslots | [ [Attendee](#attendee) ] |

### /auth/{provider}

#### POST
##### Summary:

Create user API access credential

##### Description:



##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| provider | path |  | Yes | string |
| body | body |  | No | object |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 |  | [UserOut](#userout) |

### Models


#### Action

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| user | string |  | No |
| Action | string |  | No |

#### Attendee

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | Yes |
| name | string |  | Yes |
| contact | string |  | Yes |
| refId | string |  | Yes |

#### Identifier

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | No |

#### UserIn

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | Yes |
| loginWith | string |  | Yes |
| accessToken | string |  | Yes |

#### UserOut

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | Yes |
| name | string |  | Yes |

#### UserSlotIn

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| to | string |  | Yes |
| from | string |  | Yes |
| timeZone | string |  | Yes |
| maxAttendees | string |  | Yes |
| calendarId | string |  | Yes |

#### UserSlotOut

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | Yes |
| to | string |  | Yes |
| from | string |  | Yes |
| status | string |  | No |

#### UserRule

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| monday | string |  | Yes |
| tuesday | string |  | No |
| wednesday | string |  | Yes |
| thursday | string |  | Yes |
| friday | string |  | Yes |
| saturday | string |  | No |
| sunday | string |  | No |
| start | string |  | Yes |
| end | string |  | Yes |
| timezone | string |  | Yes |
| ignoredStartTimes | [ string ] |  | No |

#### Meeting

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| attendees | [ string ] |  | No |
| awaitingAction | [ [Action](#action) ] |  | No |
| id | string |  | No |
| inviter | [UserOut](#userout) |  | No |
| slots | [  ] |  | No |
| status | string |  | No |
| title | string |  | No |
| type | string |  | No |

#### MeetingOut

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | Yes |
| title | string |  | Yes |
| inviter | string |  | Yes |
| invitees | [ string ] |  | Yes |
| slots | [ [SlotOut](#slotout) ] |  | No |

#### SlotIn

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| from | string |  | No |
| to | string |  | No |
| timeZone | string |  | No |
| attendees | [ string ] |  | No |

#### SlotUpdate

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| from | string |  | No |
| to | string |  | No |
| timeZone | string |  | No |
| attendees | [ string ] |  | No |
| status | string | One of 'pending', 'confirmed' or 'canceled' | No |

#### SlotOut

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | No |
| from | string |  | No |
| to | string |  | No |
| timeZone | string |  | No |
| attendees | [ string ] |  | No |
| status | string | One of 'pending', 'confirmed' or 'canceled' | No |

#### EmptySlot

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| to | string |  | No |
| from | string |  | No |

#### Event

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| title | string |  | No |
| to | string |  | No |
| from | string |  | No |

#### OmakaseIn

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| userId | string |  | No |
| startDate | string |  | No |
| endDate | string |  | No |
| duration | integer |  | No |
| workingHourTimeZone | string |  | No |
| attendees | [ string ] |  | No |
