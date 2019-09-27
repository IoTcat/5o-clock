# 5o-clock

## API

 - `/api/getUsrInfo.php`:

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
usr | string | usrID | xiaotian

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | Bad Connection
data | object | request data | {}
data.usrStatus | string | user status | null
data.usrGroup | string | user group id | dj8r9de3


**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**data.usrStatus List**

name | description 
:---:|:--:|
null | no such user
holding | is holding a register
joining | is joining a register
inGroup | is already in a group
