Invites
============
Invites is a way to pre-register visitors in Teamgo

* [Get an Token](#get-token "This will return a token for access to invite.")
* [Get an Invite](#get-invite "This will return a specific invite.")
* [Create Invite](#create-invite "Create an invite with attendees.")
* [Update Invite](#update-invite "This will update a specific invite.")
* [Delete Invite](#delete-invite "This will delete a specific invite.")

Get Token
------------

**Resources**
* ```GET /authenticate``` get a token

**Example Request**
```shell
curl https://api.teamgo.co/authenticate \
  -H Authorization API_KEY: \
  -H 'Accept: application/json' \
```

**Example Response**
```json
{
    "status": "OK",
    "code": 200,
    "messages": "authentication.SUCCESSFUL_AUTHENTICATION",
    "data": {
        "token": "IudJ3HXTKS8Az+geK40UyIYJleQ1YwJ9KmYj1Xqt3rh84kjPBIe2+9dSVcn9FYtRdxzZ7DeASrEb4Fxv0BeigMJzTCcZTDB4MjVmPMxW/NuULBUWrSQMnR+uiP+TUK9Zxd5+B/SvJlD2YcPf86OVacVE5QQOBRXG6OOTzs17DF5ROmHUlghR30IrqZfcUb1uBkDu2+nuaQ9LC8Fp1j0jEIoakbzNB8u122/p85D45OdZO100a+1zDziv+50AtTLBmRym7/oxdWV2Lb54z20UuAKrf3JE8DxvhL+N",
        "company": {
            "id": 10714518,
            "name": "thuan sub5"
        }
    }
}
```
Get Invite
------------

**Resources**
* ```GET /invites/:id``` get a specified booking

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
  -H Authorization Bearer TOKEN: \
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
 -H Authorization Bearer TOKEN: \
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
* ```PUT /invites/:id``` update an invite

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
 -H Authorization Bearer TOKEN: \
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
* ```DELETE /invites/:id``` delete an invite

**Example Request**
```shell
curl https://api.teamgo.co/v1/invite/1 \
 -H Authorization Bearer TOKEN: \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'User-Agent: APP_VENDOR_NAME (APP_VENDOR_EMAIL)' \
  -X DELETE
```

**Example Response**
 A status code of 204 no content will be returned if successful
