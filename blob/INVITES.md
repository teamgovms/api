Invites
============
Invites is a way to pre-register visitors in Teamgo

* [Get an Invite](#get-invite "This will return a specific invite.")
* [Create Invite](#create-invite "Create an invite with attendees.")
* [Update Invite](#update-invite "This will update a specific invite.")
* [Delete Invite](#delete-invite "This will delete a specific invite.")


Get Invite
------------

**Resources**
* ```GET /invites/:id``` get a specified booking

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
  -u API_KEY: \
  -H 'Accept: application/json' \
  -H 'User-Agent: APP_VENDOR_NAME (APP_VENDOR_EMAIL)'
```

**Example Response**
```json
{
  "id": 1,
  "created_at": "2019-05-13T14:23:16Z",
  "updated_at": "2019-05-14T14:26:13Z",
  "start": "2019-06-10T12:00:00Z",
  "end": "2019-06-10T13:00:00Z",
  "title": "Sales meeting",
  "checkin": "2019-06-10T13:00:00Z",
  "checkout": null,
  "send_reminder":true,
  "send_qrcode": true,
  "send_preregistration": false,
  "location": {
    "name":"Adelaide Head Office",
    "address":"Level 2, 44 Pirie Strett, Adelaide, SA 5000"
  },
  "attendees": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@example.com",
        "mobile":"+6104312345678",
        "language":"EN",
        "custom_fields": [
            {"Would you like coffee": "No"},
            {"Room number": 11},
            {"Guest type": "VIP"}
         ]
      },
      {"uid":124,
        "first_name":"Jane",
        "last_name":"Smith",
        "email":"jane@example.com",
        "mobile":"+6104312345679",
        "language":"EN",
        "custom_fields": [
            {"Would you like coffee": "Yes"},
            {"Room number": 11},
            {"Guest Type": "VIP"}
         ]
      }
  ],
  "hosts": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@example.com",
        "mobile":"+6104312345678"
      },
      {"uid":124,
        "first_name":"Jane",
        "last_name":"Smith",
        "email":"jane@example.com",
        "mobile":"+6104312345679"
      }
  ],
  "notes": "Please bring drinks",
  "status" "Active|Checked-In|Checked-Out|Not Coming"

}
```



Create Invite
------------

**Resources**
* ```POST /invites``` create an invite

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite \
 -u API_KEY: \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'User-Agent: APP_VENDOR_NAME (APP_VENDOR_EMAIL)' \
  -d '{ "start": 
    "2019-06-10T12:00:00Z", 
    "end": "2019-06-10T13:00:00Z", 
    "title": "Sales meeting", 
    "
    "attendees": [{"first_name": "John", "last_name": "Smith", "email": "john@example.com", "language":"EN", 
     "send_reminder":true, "send_qrcode": true,
      "custom_fields": [{"Room number": 11}, {"Guest type": "VIP"}}]
     ],
    "hosts": [{"email": "john@company.com"}]
    }' \
  -X POST
```

**Example Response**
```json
{
  "id": 2,
  "created_at": "2019-05-13T14:23:16Z",
  "updated_at": "2019-05-14T14:26:13Z",
  "title": "Sales meeting", 
  "start": "2019-06-10T12:00:00Z",
  "end": "2019-06-10T13:00:00Z",
  "checkin": "2019-06-10T13:00:00Z",
  "checkout": null,
  "send_reminder":true,
  "send_qrcode": true,
  "send_preregistration": false,
  "location": {
    "name":"Adelaide Head Office",
    "address":"Level 2, 44 Pirie Strett, Adelaide, SA 5000"
  },
  "attendees": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@example.com",
        "mobile":"+6104312345678",
        "language":"EN",
        "custom_fields": [
            {"Would you like coffee": "No"},
            {"Room number": 11},
            {"Guest type": "VIP"}
         ]
      }
  ],
  "hosts": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@company.com",
        "mobile":"+6104312345678"
      }
  ],
  "notes": "",
  "status" "Active"
}
```


Update Invite
------------

**Resources**
* ```PUT /invites/:id``` create an invite

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
 -u API_KEY: \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'User-Agent: APP_VENDOR_NAME (APP_VENDOR_EMAIL)' \
  -d '{ "start": "2019-06-10T13:00:00Z", 
    "end": "2019-06-10T14:00:00Z", 
    "title": "Sales meeting with Sarah", 
    }' \
  -X PUT
```

**Example Response**
```json
{
  "id": 2,
  "created_at": "2019-05-13T14:23:16Z",
  "updated_at": "2019-05-14T14:26:13Z",
  "title": "Sales meeting with Sarah", 
  "start": "2019-06-10T13:00:00Z",
  "end": "2019-06-10T14:00:00Z",
  "checkin": "2019-06-10T13:00:00Z",
  "checkout": null,
  "send_reminder":true,
  "send_qrcode": true,
  "send_preregistration": false,
  "location": {
    "name":"Adelaide Head Office",
    "address":"Level 2, 44 Pirie Strett, Adelaide, SA 5000"
  },
  "attendees": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@example.com",
        "mobile":"+6104312345678",
        "language":"EN",
        "custom_fields": [
            {"Would you like coffee": "No"},
            {"Room number": 11},
            {"Guest type": "VIP"}
         ]
      }
  ],
  "hosts": [
      {"uid":123,
        "first_name":"John",
        "last_name":"Smith",
        "email":"john@company.com",
        "mobile":"+6104312345678"
      }
  ],
  "notes": "",
  "status" "Active"
}
```


Delete Invite
------------

**Resources**
* ```DELETE /invites/:id``` create an invite

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
 -u API_KEY: \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'User-Agent: APP_VENDOR_NAME (APP_VENDOR_EMAIL)' \
  -X DELETE
```

**Example Response**
 A status code of 204 no content will be returned if successful
