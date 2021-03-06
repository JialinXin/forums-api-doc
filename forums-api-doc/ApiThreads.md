# Forums threads
The Forums APIs use an API key which is passed through the x-ms-apikey header. To obtain an API key please contact msdnsupp@microsoft.com.

## Get thread details

```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads/{id}
```

| Parameter (URL)   | Type     | Default | Notes
|:------------|:--------:|:-------:|:----------------------------------------------------------------------------------------------------------------------------
| id          | string   |         | Thread id

#### Header
```header
x-ms-apikey: {API-KEY}
```

### By thread id

#### Sample request
```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2
```

#### Sample response

*Status code: 200*
```json
{
    "hasMore" : false,
    "values" : [ 
        {
            "id":"b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "title":"How to get the results in sql as pivot pleas?",
            "url": "https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "webUrl": "http://social.msdn.microsoft.com/forums/en-us/b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "type": "Question",
			"state": "answered",
            "hasCode": true,
            "isLocked": false,
            "created":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "lastContentChangeOrAction": "2013-03-27T20:41:29.3160342Z",
			"lastContentChangeOrActionBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
			},
            "answers": 0,
            "proposedAnswers": 0,
			"views":300,
            "isAbusive":false,
            "abusiveMessages":0,
            "isHelpful": false,
            "lastReply":"2013-03-29T05:29:06.3160342Z",
            "lastReplyMessageId":"b6dc7be9-9ab2-49e5-89a1-748a1da705e3",
            "forum": {
                "id":"6a68166e-b521-48a8-9454-ec36622eb8ae",
                "url": "https://forumsapi.contentservices.msdn.microsoft.com/forums/6a68166e-b521-48a8-9454-ec36622eb8ae",
                "webUrl": "http://social.msdn.microsoft.com/Forums/en-US/home?forum=fsharpgeneral",
                "type": "forum",
                "displayName":"F#",
				"name": "fsharp"
            },
			"votes": 10,
			"body" : "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;",
			"repliesCount": 2,
			"repliesUrl": "https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2/replies"
        }
    ]
}
```

## search threads

```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/forums/threads[?id={string}[,{string}]&page={integer}&pageSize={integer}&search={string}&createdById={string}&createdByName={string}&repliedById={string}&repliedByName={string}&forumId={string}&forumName={string}&categoryId={string}&categoryName={string}[,{string}]&type={string}&state={string}&createdFrom={string}&createdTo={string}&contentChangeOrActionFrom={string}&contentChangeOrActionTo={string}&sort={string}&brand={string}&locale={integer}&hasCode={boolean}&hasNoReplies={boolean}&isAbusive={boolean}&isHelpful={boolean}&minReplies={integer}&maxReplies={integer}&api-version={string}]
```

| Parameter (Query)     | Type     | Default | Notes
|:----------------|:--------:|:-------:|:----------------------------------------------------------------------------------------------------------------------------
| id              | string   |         | The id of a thread.  A comma-separated list of values may be supplied to return multiple threads by id.
| search          | string   |         | A free text search string.  Threads whose title or posts contain the text will be returned.
| createdByUserId | string   |         | Id of the user who created a thread.  A comma-separated list of users may be supplied to retrieve threads created by any of the users.
| createdByUserName  | string   |         | Name of the user who created a thread.  A comma-separated list of users may be supplied to retrieve threads created by any of the users.
| postedByUserId  | string   |         | Id of a user who created or replied to a thread.  A comma-separated list of users may be supplied.
| postedByUserName   | string   |         | Name of a user who created or replied to a thread.  A comma-separated list of users may be supplied.
| forumId           | string   |         | The id of a forum.  Threads that where created in this forum will be returned.  A comma-separate list of values may be supplied to filter by multiple forums. 
| forumName           | string   |         | The url name of a forum.  Threads that where created in this forum will be returned.  A comma-separate list of values may be supplied to filter by multiple forums. 
| categoryId        | string   |         | The id of a category. Threads that where created in this category will be returned. A comma-separate list of values may be supplied to filter by multiple categories.  
| categoryName        | string   |         | The name a category. Threads that where created in this category will be returned. A comma-separate list of values may be supplied to filter by multiple categories. 
| type			  | string	 |		   | The thread type.  May be one of the following values: "discussion", "question".
| state           | string   |         | The question state string.  May be one of the following values: "unanswered", "proposed", "answered".  This value will be null for discussion-type threads. 
| brand           | string   |         | The brand in which the thread occurs.  May be one of the following values: "microsoft", "msdn", "technet".
| locale          | integer/string |   | The locale of the thread.  The locale may be specified as either the LCID integer value, or as a locale string.  For example, to return english threads only, one could supply either ?locale=1033 or ?local=en-us
| hasCode         | boolean  |         | Specifies whether or not the thread has code.
| isHelpful       | boolean  |         | Specifies whether or not the thread has been marked as helpful.
| hasNoReplies    | boolean  |         | Specifies whether or not the thread has replies.
| isAbusive       | boolean  |         | Specifies whether or not the thread has a reply that has been marked as abusive.
| minReplies      | integer  | 0       | Specifies the minimum number of replies a thread must contain.  Only threads containing at least this many replies will be returned.
| createdFrom  | dateTime |         | The minimum thread creation time.  Only threads that were created after this date and time will be returned.
| createdTo    | dateTime |         | The maximum thread creation time.  Only threads that were created before this date and time will be returned.
| contentChangeOrActionFrom  | dateTime |         | The minimum thread last content change or action time.  Only threads that have been edited, had a new or edited reply, had voting activity, had a reply proposed or marked as an answer, been reported as abusive, had its type changed, or been moved, split or merged after this date and time will be returned.
| contentChangeOrActionTo    | dateTime |         | The maximum thread last content change or action time.  Only threads that have not been edited, had a new or edited reply, had voting activity, had a reply proposed or marked as an answer, been reported as abusive, had its type changed, or been moved, split or merged after this date and time will be returned.
| sort            | string   | lastPostDate | The sort order of returned threads.  Valid values are "createdDate", "replies", "lastPostDate", "votes", "lastContentChangeOrActionDate".
| order           | string   | desc    | The sort order of returned threads.  Valid values are "asc" and "desc".
| page            | integer  | 1       | When the number of results exceeds the maximum page size, then the page parameter indicates which page of results to return.  This value is unit-based, meaning that the first page of results is indicated by ?page=1
| pageSize        | integer  | 50      | The number of results to return per page.  This value cannot exceed 50.
| api-version             | string   |         | The version of the API to use. Refer to [Versioning](#versioning) for more details.

### By multiple IDs

#### Sample request
```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads?threadId=b16f7cb3-867a-4156-953c-3efc7a050ee2,515bed28-1ba8-4e2e-9626-6538df9fe218
```

#### Sample response

*Status code: 200*
```json
{
    "hasMore" : false,
    "values" : [ 
        {
            "id":"b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "title":"How to get the results in sql as pivot pleas?",
            "url": "https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "webUrl": "http://social.msdn.microsoft.com/forums/en-us/b16f7cb3-867a-4156-953c-3efc7a050ee2",
            "type":"Question",
			"state": "answered",
            "hasCode":true,
            "isLocked":false,
            "created":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "lastContentChangeOrAction": "2013-03-27T20:41:29.3160342Z",
			"lastContentChangeOrActionBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
			},
            "answers":1,
            "proposedAnswers":1,
			"views":300,
            "isAbusive":false,
            "abusiveMessages":0,
            "isHelpful":false,
            "lastReply":"2013-03-29T05:29:06.3160342Z",
            "lastReplyMessageId":"b6dc7be9-9ab2-49e5-89a1-748a1da705e3",
            "forum":{
                "id":"6a68166e-b521-48a8-9454-ec36622eb8ae",
                "url": "https://forumsapi.contentservices.msdn.microsoft.com/forums/6a68166e-b521-48a8-9454-ec36622eb8ae",
                "webUrl": "http://social.msdn.microsoft.com/Forums/en-US/home?forum=fsharpgeneral",
                "type": "forum",
                "displayName":"F#",
				"name":"fsharp"
            },
			"votes": 10,
			"body" : "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;",
			"repliesCount": 5,
			"repliesURL": "https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2/replies"
        }
    ]
}
```


### By search query

#### Sample request
```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads?createdBy=4d39b289-6acc-4cd1-97c4-6535b819671f&search=jscript&forumId=42b91635-70bd-49ab-a143-ef01bb5186d6&brand=microsoft&hasCode=1&helpful=0&noreplies=0&minReplies=1&contentChangeOrActionFrom=2009-03-24T21:32:46&contentChangeOrActionTo=2014-01-01&page=1&pageSize=50
```

#### Sample response

*Status code: 200*
```json
{
    "hasMore" : false,
    "values" : [ 
        {
            "id":"6d14c435-b96c-4c5e-a7f3-fa9af42520de",
            "title":"R4: How to use RetrieveMultiple to retrieve only active records using Jscript?",
            "url": "https://forumsapi.contentservices.msdn.microsoft.com/threads/6d14c435-b96c-4c5e-a7f3-fa9af42520de",
            "webUrl": "http://social.msdn.microsoft.com/forums/en-us/6d14c435-b96c-4c5e-a7f3-fa9af42520de",
            "type":"Question",
			"state": "unanswered",
            "hasCode":false,
            "isLocked":false,
            "created":"2009-04-16T11:37:17.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "lastContentChangeOrAction": "2013-03-27T20:41:29.3160342Z",
			"lastContentChangeOrActionBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
			},
            "answers":0,
            "proposedAnswers":0,
			"views":300,
            "isAbusive":false,
            "abusiveMessages":0,
            "isHelpful":false,
            "lastReply":"2009-04-16T12:16:28.3160342Z",
            "lastReplyMessageId":"c63c1240-099f-49ea-aa10-115eb587eaff",
            "forum":{
                "id":"42b91635-70bd-49ab-a143-ef01bb5186d6",
                "url": "https://forumsapi.contentservices.msdn.microsoft.com/forums/6a68166e-b521-48a8-9454-ec36622eb8ae",
                "webUrl": "http://social.msdn.microsoft.com/Forums/en-US/home?forum=fsharpgeneral",
                "type": "forum",
                "displayName":"F#",
				"name":"fsharp"
            },
			"votes": 10,
			"body" : "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;",
			"repliesCount": 4,
			"repliesURL": "https://forumsapi.contentservices.msdn.microsoft.com/threads/6d14c435-b96c-4c5e-a7f3-fa9af42520de/replies"
        },
        {
            "id":"44a9f572-2a47-49a3-b419-f373805bc788",
            "title":"how do i create new CRM records using javascript??",
            "url": "https://forumsapi.contentservices.msdn.microsoft.com/threads/44a9f572-2a47-49a3-b419-f373805bc788",
            "webUrl": "http://social.msdn.microsoft.com/forums/en-us/44a9f572-2a47-49a3-b419-f373805bc788",
            "type":"Discussion",
			"state": null,
            "hasCode":false,
            "isLocked":false,
            "created":"2009-04-22T07:49:16.3160342Z",
            "createdBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "lastContentChangeOrAction": "2013-03-27T20:41:29.3160342Z",
			"lastContentChangeOrActionBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
			},
            "answers":4,
            "proposedAnswers":0,
			"views":300,
            "isAbusive":false,
            "abusiveMessages":0,
            "isHelpful":false,
            "lastReplyDate":"2009-04-23T19:07:22.3160342Z",
            "lastReplyMessageId":"75895d8e-f106-4198-b88c-56a6c7b9d79b",
            "categories":[ 
				{ 
					"categoryId": "1794d07f-9d4e-4dc0-8c1c-8bfe9d5e0bce", 
					"name" : "officedev", 
					"displayName":"Microsoft Office for Developers", 
					"locale":"en-us" 
				} 
			],
            "locales":["en","en-US"],
            "forum":{
                "id":"42b91635-70bd-49ab-a143-ef01bb5186d6",
                "url": "https://forumsapi.contentservices.msdn.microsoft.com/forums/6a68166e-b521-48a8-9454-ec36622eb8ae",
                "webUrl": "http://social.msdn.microsoft.com/Forums/en-US/home?forum=fsharpgeneral",
           		"type": "forum",
                "displayName":"F#",
				"name":"fsharp"
            },
			"votes": 10,
			"body" : "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;",
			"repliesCount": 7,
			"repliesURL": "https://forumsapi.contentservices.msdn.microsoft.com/threads/44a9f572-2a47-49a3-b419-f373805bc788/replies"
        }
    ]
}
```

## Create a thread

The thread **title**, **body** and **api-version** are required fields. Creating a new thread uses LiveConnect authentication. More information about this can be found https://github.com/liveservices. A valid User Access Token is required. This value is passed with the x-ms-useraccesstoken header.


```httprequest
POST https://forumsapi.contentservices.msdn.microsoft.com/threads?api-version={string}
```

```json
{

    "forum" : { string },
	"type"  : { string },
	"title" : { string },
	"body"  : { string },
	"alertMe" : { bool },
 
}
```

| Parameter (URL)  | Type     | Default  | Notes
|:------------|:--------:|:---------|:---------------------------------------------------------------------------------------
| api-version  | string   |         | The version of the API to use. Refer to [Versioning](#versioning) for more details.
| Request body
| forum       | string   |          | id or url name of the forum in which you are creating
| type        | string   | Question | Type of thread being created. Valid values are 'Question' or 'Discussion'. 
| title       | string   |          | Title of the thread being created 
| body        | string   |          | Body of the thread being created
| alertMe     | bool     | True     | Configures an alert for the user posting the thread


#### Sample request

```httprequest
POST https://forumsapi.contentservices.msdn.microsoft.com/threads?api-version=1.0-preview
```

```json
{

    "forum" : "wpf",
	"title" : "Transfer data Between two Usercontrol inside of Mainwindows",
	"body"  : "<p>Goal:<br />The input data that is located inside of the textbox search (usercontrol_menu.xaml) shall be transferred and then to be used inside of usercontrol_number1.xaml. </p><p>Problem:<br />I don't know what to do. What tactics and how to do it? From your experience, how should you do it? </p><p>Information:<br />- MainWindows.xaml is located in a separated project.</p><p></p><p><img alt="" src="http://social.msdn.microsoft.com/Forums/getfile/483597" /></p><br />"
 
}
``` 
#### Response

*status code: 201*
```json
{
    "hasMore" : false,
    "values" : [ 
        {
            "id":"906c5f4a-4065-46e2-a8f9-dec37d235418",
            "title":"Transfer data Between two Usercontrol inside of Mainwindows",
            "url": "https://forumsapi.contentservices.msdn.microsoft.com/threads/906c5f4a-4065-46e2-a8f9-dec37d235418",
            "webUrl": "http://social.msdn.microsoft.com/forums/en-us/906c5f4a-4065-46e2-a8f9-dec37d235418",
            "type": "Question",
			"state": "unanswered",
            "hasCode": true,
            "isLocked": false,
            "created":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "lastContentChangeOrAction": "2013-03-27T20:41:29.3160342Z",
			"lastContentChangeOrActionBy": {
                "userId" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
			},
            "answers": 0,
            "proposedAnswers": 0,
			"views":0,
            "isAbusive":false,
            "abusiveMessages":0,
            "isHelpful": false,
            "lastReply": null,
            "lastReplyMessageId": null,
            "forum": {
                "id":"6a68166e-b521-48a8-9454-ec36622eb8ae",
                "url": "https://forumsapi.contentservices.msdn.microsoft.com/forums/6a68166e-b521-48a8-9454-ec36622eb8ae",
                "webUrl": "http://social.msdn.microsoft.com/Forums/en-US/home?forum=wpf",
                "type": "forum",
                "displayName":"Windows Presentation Foundation (WPF)"
            },
			"votes": 0,
			"body" : "<p>Goal:<br />The input data that is located inside of the textbox search (usercontrol_menu.xaml) shall be transferred and then to be used inside of usercontrol_number1.xaml. </p><p>Problem:<br />I don't know what to do. What tactics and how to do it? From your experience, how should you do it? </p><p>Information:<br />- MainWindows.xaml is located in a separated project.</p><p></p><p><img alt="" src="http://social.msdn.microsoft.com/Forums/getfile/483597" /></p><br />",
			"repliesCount": 0,
			"repliesURL": "https://forumsapi.contentservices.msdn.microsoft.com/threads/906c5f4a-4065-46e2-a8f9-dec37d235418/replies"
        }
    ]
}
```

## Get thread replies

```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads/{id}/replies
```

| Parameter (URL)   | Type     | Default | Notes
|:------------|:--------:|:-------:|:----------------------------------------------------------------------------------------------------------------------------
| id          | string    |            | Thread id

#### Sample request
```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/threads/b16f7cb3-867a-4156-953c-3efc7a050ee2/replies
```
#### Sample response

*Status code: 200*
```json
{
	"hasMore" : false,
	"values" : [
		{
			"id": "735f85dd-8e6a-43ea-8d0c-f1641d477d73",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
            	"id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
             },
             "votes": 10,
             "isAbusive": false,
             "isAnswer": false,
             "parentId": null,
             "body": "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;"
        },
        {
            "id": "11e62df7-9938-4547-a5cc-8ea1a3dfd7b1",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "votes": 10,
            "isAbusive": false,
            "isAnswer": false,
            "parentId": "735f85dd-8e6a-43ea-8d0c-f1641d477d73",
              "body": "&lt;P&gt;Para testar se uma data &#233; v&#225;lida, vc pode utilizar um bloco try/catch&lt;/P&gt;\r\n&lt;P&gt;String dataString = &quot;21/08/2006&quot;;&lt;/P&gt;\r\n&lt;P&gt;DateTime data;&lt;/P&gt;\r\n&lt;P&gt;try&lt;/P&gt;\r\n&lt;P&gt;{&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; data = Convert.ToDateTime(dataString);&lt;/P&gt;\r\n&lt;P&gt;}&lt;/P&gt;\r\n&lt;P&gt;catch(Exception ex)&lt;/P&gt;\r\n&lt;P&gt;{&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; MessageBox.Show(&quot;Data inv&#225;lida!&quot;);&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; return;&lt;/P&gt;\r\n&lt;P&gt;}&lt;/P&gt;"
        },
        {
            "id": "8c3f8d56-6966-4477-bbd4-728c03d9329e",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "votes": 10,
            "isAbusive": false,
            "isAnswer": false,
            "parentId": null,
            "body": "&lt;p&gt;Olha s&#243;, vc t&#225; fazendo uma pequena confus&#227;o ai.&lt;/p&gt;\r\n&lt;p&gt;&lt;font face=Verdana&gt;1&#186; - As datas s&#227;o n&#250;meros, s&#227;o armazenadas assim.&lt;/font&gt;&lt;/p&gt;\r\n&lt;p&gt;&lt;font face=Verdana&gt;2&#186; - Quando vc quer mostrar uma data, vc deve formata-la conforme lhe convier.&lt;/font&gt;&lt;/p&gt;\r\n&lt;p&gt;&lt;font face=Verdana&gt;3&#186; - Existem v&#225;rios formatos de apresenta&#231;&#227;o de datas, mas o n&#250;mero guardado dentro da vari&#225;vel data &#233; sempre o mesmo.&lt;/font&gt;&lt;/p&gt;\r\n&lt;p&gt;&lt;font face=Verdana&gt;Ent&#227;o, se vc quer comparar uma data, subtrair, etc... vc n&#227;o precisa formata-la para fazer isso. O erro est&#225; acontecendo porque vc est&#225; pegando um campo data e formatando para&#160;ter a saida igual a dd/MM/yyyy, contudo a instru&#231;&#227;o if requer uma condi&#231;&#227;o verdadeira ou falsa para tomar uma decis&#227;o. Logo vc est&#225; retornando a data formatada, ou seja, uma string e&#160;a instru&#231;&#227;o if requer uma condi&#231;&#227;o booleana. VC at&#233; poderia fazer isso:&lt;/font&gt;&lt;/p&gt;\r\n&lt;p&gt;&lt;font color=&quot;#0000ff&quot; size=2&gt;&#160;&lt;/font&gt;if&lt;font size=2&gt; (tbFinanciamentoFilial.DataInicioVigencia.ToString(&lt;/font&gt;&lt;font color=&quot;#800000&quot; size=2&gt;&amp;quot;dd/MM/yyyy&amp;quot;&lt;/font&gt;&lt;font size=2&gt;) == &amp;quot;21/08/2006&amp;quot;)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;retorno = &lt;/font&gt;&lt;font color=&quot;#0000ff&quot; size=2&gt;false&lt;/font&gt;&lt;font size=2&gt;;&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;E est&#225; &lt;/p&gt;\r\n&lt;p&gt;&#160;&lt;/p&gt;&lt;/font&gt;"
        }
	]
}
``` 


## Create thread replies
The thread **id**, **body** and **api-version** are required fields. Replying to a thread uses LiveConnect authentication. More information about this can be found https://github.com/liveservices. A valid User Access Token is required. This value is passed with the x-ms-useraccesstoken header.

```httprequest
POST https://forumsapi.contentservices.msdn.microsoft.com/threads/{id}/replies?api-version={string}
```

```json
{

    "body" : { string },
	"parentId"  : { string },
	"alertMe" : { bool },
 
}
```

| Parameter (URL)   | Type     | Default | Notes
|:------------|:--------:|:-------:|:----------------------------------------------------------------------------------------------------------------------------
| id          | string    |            | Thread id
| api-version  | string   |         | The version of the API to use. Refer to [Versioning](#versioning) for more details.
| Request body
| body        | string    |            | Body of the reply being created. This string may contain html entities that will be rendered in web views and returned verbatim by the api. Example html to be displayed as such should be html encoded by the user prior to posting.
| parentId    | string    | Thread id  | Id of the the thread or reply which the post will be created under 
| alertMe     | bool      | True       | Configures an alert for the user posting the reply




#### Sample request
```httprequest
POST https://forumsapi.contentservices.msdn.microsoft.com/threads/65d55f93-d262-4526-b53c-17336df4baed/replies?api-version=1.0-preview
```
```json
{

    "body" : "Thank you again for your help!!! I have a concrete sample and I will add it as a new question.",
	"parentId": "dfb5c35a-e280-431e-bf0a-00f7339c07a"
	"alertMe" : True
 
}
``` 

#### Response

*status code: 201*
```json
{
	"hasMore" : false,
	"values" : [
		{
			"id": "dfb5c35a-e280-431e-bf0a-00f7339c07a",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
            	"id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
             },
             "votes": 10,
             "isAbusive": false,
             "isAnswer": false,
             "parentId": null,
             "body": "&lt;p&gt;Uhmm !!! entendi o que vc queria !!! &lt;/p&gt;\r\n&lt;p&gt;para saber se a data &#233; v&#225;lida eu fa&#231;o de uma forma muito simples , &lt;/p&gt;\r\n&lt;p&gt;// pego a data que o cara digitou e tento converter para DateTime , se funcionar &#233; v&#225;lida , se n&#227;o , a data esta inv&#225;lida ... veja como faz ...&lt;/p&gt;\r\n&lt;p&gt;public static bool DataV&#225;lida(string Texto)&lt;/p&gt;\r\n&lt;p&gt;{&lt;/p&gt;\r\n&lt;p&gt;&#160; try&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; DateTime Dt = Convert.ToDateTime(texto);&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return true;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;&#160; catch&lt;/p&gt;\r\n&lt;p&gt;&#160; {&lt;/p&gt;\r\n&lt;p&gt;&#160;&#160;&#160; return false;&lt;/p&gt;\r\n&lt;p&gt;&#160; }&lt;/p&gt;\r\n&lt;p&gt;}&lt;/p&gt;\r\n&lt;p&gt;... t+&lt;/p&gt;"
        },
        {
            "id": "11e62df7-9938-4547-a5cc-8ea1a3dfd7b1",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "votes": 10,
            "isAbusive": false,
            "isAnswer": false,
            "parentId": "735f85dd-8e6a-43ea-8d0c-f1641d477d73",
              "body": "&lt;P&gt;Para testar se uma data &#233; v&#225;lida, vc pode utilizar um bloco try/catch&lt;/P&gt;\r\n&lt;P&gt;String dataString = &quot;21/08/2006&quot;;&lt;/P&gt;\r\n&lt;P&gt;DateTime data;&lt;/P&gt;\r\n&lt;P&gt;try&lt;/P&gt;\r\n&lt;P&gt;{&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; data = Convert.ToDateTime(dataString);&lt;/P&gt;\r\n&lt;P&gt;}&lt;/P&gt;\r\n&lt;P&gt;catch(Exception ex)&lt;/P&gt;\r\n&lt;P&gt;{&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; MessageBox.Show(&quot;Data inv&#225;lida!&quot;);&lt;/P&gt;\r\n&lt;P&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp; return;&lt;/P&gt;\r\n&lt;P&gt;}&lt;/P&gt;"
        },
        {
            "id": "8c3f8d56-6966-4477-bbd4-728c03d9329e",
            "created":"2013-03-27T20:41:29.3160342Z",
            "lastModified":"2013-03-27T20:41:29.3160342Z",
            "createdBy": {
                "id" : "502f2af9-2e96-47d7-9bfa-4769814ba9e6",
				"displayName":"Nigel Beasley",
                "url" : "https://forumsapi.contentservices.msdn.microsoft.com/users/502f2af9-2e96-47d7-9bfa-4769814ba9e6"
            },
            "votes": 10,
            "isAbusive": false,
            "isAnswer": false,
            "parentId": dfb5c35a-e280-431e-bf0a-00f7339c07ass,
            "body": "Thank you again for your help!!! I have a concrete sample and I will add it as a new question."
        }
	]
}
``` 

## Errors

REST API operations for forums services return standard HTTP status codes, as defined in the HTTP/1.1 Status Code Definitions.  API operations my also return additional error information in the response body.

The body of the error response follows the JSON format shown here.

#### Sample response

```json
{
    "errors" : [
            "Unrecognized parameter: 'numVotes'.",
            "Unrecognized parameter: '042870'."        
    ]
}
```
<a name="versioning"></a>
## Versioning

The Forums API is versioned to ensure client applications and services work as APIs are added and changed. The current version of the API set is 1.0-preview. Specifying API Version is optional for GET requests and required for POST/PUT/UPDATE/DELETE. If not specified, it defaults to the latest. API version can be specified either in the header of the HTTP request or as a URL query parameter.

HTTP request header:
```httprequest
Accept: application/json;api-version=1.0-preview
```

Query parameter:
```httprequest
GET https://forumsapi.contentservices.msdn.microsoft.com/forums/7a9b8c49-06ac-44fe-b0fd-81485bd31386?api-version=1.0-preview
```