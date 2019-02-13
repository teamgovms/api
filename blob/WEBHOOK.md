Webhook
=======

Webhook events are triggered in real time whenever there is a sign-in or sign-out activity.

Webhook can be created for the following events:
- Visitor checkin 
- Visitor checkout 
- Visitor request for assistance 
- Delivery 
- Import Successful 
- Import Failed

Teamgo perform HTTPS request to the specified URL using POST with the following data:

**Data**
<table>
    <thead>
        <tr>
            <th>Field Name</th>
            <th>Data Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>type</td>
            <td><code>string</code></td>
            <td>Webhook type. One of <code>'checkin'</code> or <code>'checkout'</code></td>
        </tr>
        <tr>
            <td>timestamp</td>
            <td><code>Unix timestamp</code></td>
            <td>Time this event triggered</td>
        </tr>
        <tr>
            <td>token</td>
            <td><code>string</code></td>
            <td>Random string</td>
        </tr>
        <tr>
            <td>signature</td>
            <td><code>string</code></td>
            <td>This is used to ensure this message comes from our
                server. This signature is derived from concatenating a timestamp with the token
                then hash it using hash_sha256 using your API Key as key. Eg: <br><code>
                    hash_sha256(concatenate(timestamp, token), <a href="https://go.teamgo.co/settings/api" target="_blank">your_api_key</a>)
                </code>
            </td>
        </tr>
        <tr>
            <td>data</td>
            <td><code>Object</code></td>
            <td>All your checkin data</td>
        </tr>
        <tr>
            <td>data.pass_id</td>
            <td><code>integer</code></td>
            <td>Unique visitor pass number</td>
        </tr>
        <tr>
            <td>data.full_name</td>
            <td><code>string</code></td>
            <td>Visitor name</td>
        </tr>
        <tr>
            <td>data.company</td>
            <td><code>string</code></td>
            <td>Vistor company name</td>
        </tr>
        <tr>
            <td>data.email</td>
            <td><code>email</code></td>
            <td>Visitor email</td>
        </tr>
        <tr>
            <td>data.meeting</td>
            <td><code>Array</code></td>
            <td>Hosts the visitor selected to meet in this format: <br><code>[{"email":"host1@example.com","full_name":"Host 1"},{"email":"host2@example.com","full_name":"Host 2"}]</code></td>
        </tr>
        <tr>
            <td>data.terminal</td>
            <td><code>string</code></td>
            <td>Terminal name</td>
        </tr>
        <tr>
            <td>data.location</td>
            <td><code>string</code></td>
            <td>Location name</td>
        </tr>
        <tr>
            <td>data.checkin_time</td>
            <td><code>ISO date</code></td>
            <td>Checkin date and time</td>
        </tr>
        <tr>
            <td>data.checkout_time</td>
            <td><code>ISO date</code></td>
            <td>Checkout date and time</td>
        </tr>
        <tr>
            <td>data.extra_fields</td>
            <td><code>Array</code></td>
            <td>Custom fields as specified in your sign-in form</td>
        </tr>
    </tbody>
</table>


Visitor/Staff Checkin and Checkout
----------------------------------
This webhook triggered when a visitor sign-in or sign-out

**Data Example**
````
{
  "type": "checkout",
  "timestamp": "1481274229",
  "token": "d368b024b8b6427263a41e7a36f0f44e",
  "signature": "8860a48a6902e4e2eef766ebf0a17c9939a29ff2043bfeb50bfc93d70bf9cbfd",
  "data": {
    "pass_id": "11249854",
    "full_name": "Bob Jones",
    "company": "Teamgo Pty Ltd",
    "email": "bobjones@example.com",
    "mobile": "+610812345678",
    "meeting": [
    	{
		"email":"host1@example.com",
		"full_name":"Host 1"
	},
    	{
		"email":"host2@example.com",
		"full_name":"Host 2"
    	}
    ],
    "terminal": "Terminal 1",
    "location": "Location 1",
    "checkin_time": "2016-12-09T08:44:46+00",
    "checkout_time": "2016-12-09T09:02:11+00",
    "extra_fields": [
	{
		"field": "Are you an American citizen?",
		"value":"Yes"
	}
    ]
  }
}
````

Request Assistance
------------------
Triggered in real time whenever there is an assitance request.

**Data Example**
````
{
  "type": "rq_assistance",
  "timestamp": "1481274229",
  "token": "d368b024b8b6427263a41e7a36f0f44e",
  "signature": "8860a48a6902e4e2eef766ebf0a17c9939a29ff2043bfeb50bfc93d70bf9cbfd",
  "data": {
    "message": "Someone is requesting assistance at Main Entrance - Headquarter",
    "terminal": "Main Entrance",
    "location": "Headquarter",
    "request_time": "2016-12-09T08:44:46+00",
  }
}
````

Delivery Check-in
-----------------
Triggered in real time whenever there is a delivery.

**Data Example**
````
{
  "type": "courier",
  "timestamp": "1481274229",
  "token": "d368b024b8b6427263a41e7a36f0f44e",
  "signature": "8860a48a6902e4e2eef766ebf0a17c9939a29ff2043bfeb50bfc93d70bf9cbfd",
  "data": {
    "message": "David Lee you have a delivery. Signature required at Main Entrance",
    "terminal": "Main Entrance",
    "location": "Headquarter",
    "host": "David Lee",
    "host_email": "david.lee@company.co"
    "request_time": "2016-12-09T08:44:46+00",
  }
}
`````

Import Status
-------------
Triggered in real time whenever there is an import user process completed.

**Data Example**
`````
{
  "type": "import_success",
  "timestamp": "1481274229",
  "token": "d368b024b8b6427263a41e7a36f0f44e",
  "signature": "8860a48a6902e4e2eef766ebf0a17c9939a29ff2043bfeb50bfc93d70bf9cbfd",
  "data": {
    "message": "Your import completed. The data is now updated on the Teamgo Dashboard.",
    "import_time": "2016-12-09T08:44:46+00",
  }
}
`````



