Time Passport API
==============================

Time Passport API is a scheduling service that assist users to manage and plan their day to day schedule. The API can be used standalone as a schedule management service or an integration with third-party applications to complement our Time Passport application.

WHY
------------------------------
Managing your time is an important aspect of your day
...
focus on what matters the most

Automatically let others know when you are available

Manage all your calendars in one place

Instantly let other people know your availability

Import events from your existing Calendar

Flexible workflows, 1 to 1, group meeting, 1 to many. Internal meeting, job interviews


How
------------------------------
time.truffle.ai/dashboard

``` js
var api = "https://asia-northeast1-schedulerly-prod.cloudfunctions.net/api/"
var path = "v0/users"
var createUser = async function(){
  const response = await fetch(`${api}${path}`, {
    method: 'POST',
    mode: 'cors',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(user)
  })
  var result = await response.json()
  console.log('result:', result)
}>
