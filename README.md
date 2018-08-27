# Device Registry Service

## Usage

All response will have the form 

```json
{
    "data": "Mixed type holding the content of the response",
    "mesage":
}
```

Subsequent response definitions will only detail the expect value of the `data file`

### List all devices

**Definition**

`GET /devices`

**Response**

- `200 OK` on success
 
 ```json
 [
     {
         "identifier": "floor-lamp",
         "name": "Floor Lamp",
         "device_type": "switch",
         "controller_gateway": "192.168.2.33"
     },
     {
         "identifier": "samsung-tv",
         "name": "Living Room TV",
         "device_type": "tv",
         "controller_gateway": "192.168.2.32"
     }
 ]
 ```

### Registering a new device

**Defintion**

`PUT /devices`

**Arguments**

- `"identifier":string` a globally unique identifier for this device
- `"name":string` a friendly name for this device
- `"device_type":string` the type of device as understodd by the client
- `"controller_gateway":string` the IP address of the device's controller

If a device with the given identifier already exists, the existing device will be overwritten.

**Response**

- `201 Create` on success

```json
{
        "identifier": "floor-lamp",
        "name": "Floor Lamp",
        "device_type": "switch",
        "controller_gateway": "192.168.2.33"
}
```

## Lookup device details

`GET /device/<identifier>`

**Response**

- `404 Not Found` if the device does not exist
- `200 OK` on success

```json
{
        "identifier": "floor-lamp",
        "name": "Floor Lamp",
        "device_type": "switch",
        "controller_gateway": "192.168.2.33"
}
```

### Delete a device

**Definition**

`DELETE /device/<identifier>`

**Response**

- `404 Not Found` if the device does not exist
- `204 No Content` on success