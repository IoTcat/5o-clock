# 5o-clock

## API

 - `/api/getUsrInfo.php`:

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
usrId | string | usrID | 89wvh4ee

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"
data | object | request data | {}
data.status | string | user status | "null"
data.id | string | user id | "89wvh4ee"
data.alias | string | user profile alias | "ben"
data.img | string | user profile pic url | "https://api.yimian.xyz/img?type=head"
data.groupId | string | user group id | "dj8r9de3"


**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**data.status List**

name | description 
:---:|:--:|
undefined | no such usr before 
null | not in process
holding | is holding a register
joining | is joining a register
inGroup | is already in a group

**Example**

```js
{
	isError: false,
	code: 200,
	msg: "",
	data: {
		status: "holding",
		id: "di3edo9s",
		alias: "小明",
		img: "https://api.yimian.xyz/img?type=head&id=3",
		groupId: "8dk3d91k"
	}

}

```



 - `/api/getGroupInfo.php`:

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
groupId | string | groupID | dk380we3

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"
data | object | request data | {}
data.status | string | group status | "null"
data.id | string | group id | "dk380we3"
data.totalNum | number | total group members number | 6
data.alias | string | group profile alias | "凤凰传奇"
data.members | array | group members | []
data.members[].id | string | userID | "dj8r9de3"
data.members[].status | string | user status | "null"
data.members[].alias | string | user profile alias | "ben"
data.members[].img | string | user profile pic url | "https://api.yimian.xyz/img?type=head"

**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**data.status List**

name | description 
:---:|:--:|
undefined | no such group 
forming | group is being formed
running | group is normally running
dismissed | group is already dimissed


**data.members[].status List**

name | description 
:---:|:--:|
undefined | no such usr before 
null | not in process
holding | is holding a register
joining | is joining a register
inGroup | is already in a group


**Example**

```js
{
	isError: false,
	code: 200,
	msg: "",
	data: {
		status: "forming",
		alias: "凤凰传奇",
		totalNum: 6,
		members: [
			{
				id: "di3edo9s",
				status: "holding",
				alias: "小明",
				img: "https://api.yimian.xyz/img?type=head&id=3"
			},
			{
				id: "dv49do9s",
				status: "joining",
				alias: "大明",
				img: "https://api.yimian.xyz/img?type=head&id=4"
			},
			{
				id: "do9sdi3e",
				status: "joining",
				alias: "二明",
				img: "https://api.yimian.xyz/img?type=head&id=5"
			}
		]
	}

}

```


 - `/api/setUsrInfo.php`:

**Method**
 - POST
 - GET

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
id | string | usrID (need to be unique) | 89wvh4ee
alias | string | user profile alias | 小明
img | string | user profile picture url | https://api.yimian.xyz/img?type=head&id=3

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"

**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**Sepcial Code List**

code | description 
:---:|:--:|
501 | User Already Exist
502 | invalid user id
503 | invalid usr alias
504 | invalid usr profile picture url


**Example**
```
/api/setUsrInfo.php?id=e23sr3ed&alias=中明&img=https://api.yimian.xyz/img?type=head&id=8
```

```js
{
	isError: false,
	code: 200,
	msg: "",
}

```



 - `/api/setNewGroup.php`:

**Method**
 - POST
 - GET

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
alias | string | group profile alias | 凤凰传奇
num | number | group total number | 7
threshold | number | system threshold | 20

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"

**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**Sepcial Code List**

code | description 
:---:|:--:|
502 | invalid group number
503 | invalid group alias
504 | invalid group threshold


**Example**
```
/api/setNewGroup.php?alias=凤凰传奇&num=7&threshold=20
```

```js
{
	isError: false,
	code: 200,
	msg: "",
}

```


 - `/api/joinGroup.php`:

**Method**
 - POST
 - GET

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
usrID | string | user ID | 89wvh4ee
groupID | string | group ID | d83jdle3

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"

**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**Sepcial Code List**

code | description 
:---:|:--:|
501 | invalid group id
502 | invalid user id
503 | user already in other group
504 | group is full
505 | group is canceled


**Example**
```
/api/joinGroup.php?groupID=e23sr3ed&usrID=d8ei3dd2
```

```js
{
	isError: false,
	code: 200,
	msg: "",
}

```


 - `/api/cancelGroup.php`:

**Method**
 - POST
 - GET

**Params**

name | type | description | example 
:---:|:--:|:--:|:---:|
usrID | string | user ID | 89wvh4ee
groupID | string | group ID | d83jdle3

**Response**

name | type | description | example 
:---:|:--:|:--:|:---:|
isError | bool | requset error | false
code | num | request status | 404
msg | string | error message | "Bad Connection"

**code List**
[status code reference](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

**Sepcial Code List**

code | description 
:---:|:--:|
501 | invalid group id
502 | invalid user id
503 | this user have no right to cancel this group
504 | group was already canceled


**Example**
```
/api/cancelGroup.php?groupID=e23sr3ed&usrID=d8ei3dd2
```

```js
{
	isError: false,
	code: 200,
	msg: "",
}

```