Time Passport API
==============================

Time Passport API is a scheduling service that assist users to manage and plan their day to day schedule. The API can be used standalone as a schedule management service or an integration with third-party applications to complement our Time Passport application.

Time Passport offers robust workflows allowing you to co-ordinate various type of meetings such as a job interviews and meetings in a One to One or One to Many format.

The need for time management tool
----------------------------------
Managing your schedule is an important aspect of your day and it's exponetially more time consuming as you get busier. Time Passport simplifies your time management process allowing you to focus on what matters the most.

Features:
* Preset your scheduled to automatically let others know when you are available
* Manage all your calendars in one place by your account with Google Calendars and other services
* Send an meeting invite with your availability
* Limit the number of attendees per a slot
* Determine best slot based on attendee availability
* Integrate Time Passport with other application

Getting Started
-----------------------------------

Sign up to our [Time Passport App](http://time.truffle.ai/dashboard)

Create Calendar

``` js
var api = "https://time.truffle.ai/api/"
var path = "v0/calendars/"
var createCalendar = async function(){
  const response = await fetch(`${api}${path}`, {
    method: 'POST',
    mode: 'cors',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(calendar)
  })
  var result = await response.json()
  console.log('result:', result)
}
createCalendar()
```
Get Calendar Slots


``` js
var api = "https://time.truffle.ai/api/"
var path = "v0/calendars/slots"
var getSlots = async function(){
  const response = await fetch(`${api}${path}`, {
    method: 'GET',
    mode: 'cors',
    headers: {
      'Content-Type': 'application/json'
    }
  })
  var result = await response.json()
  console.log('result:', result)
}
getSlots()
```
