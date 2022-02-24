### Versions
```
BASE:
https://quizizz.com
https://staging.quizizz.com
https://dev.quizizz.com
http://localhost:3000

SOCKET:
https://socket.quizizz.com
https://staging.quizizz.com
https://dev-socket.quizizz.com
https://dev-socket.quizizz.com

GAME:
https://game.quizizz.com
https://staging.quizizz.com
https://dev.quizizz.com
https://dev.quizizz.com

REQUEST:
https://quizizz.com
https://staging.quizizz.com
https://dev.quizizz.com/_api/main
http://localhost:3000

NOTIFICATION_BASE:
https://notif.quizizz.com
https://notif.quizizz.com
https://dev-services.quizizz.com
https://dev-services.quizizz.com
```

### API versions
```
https://quizizz.com/api/main
https://quizizz.com/api/rapydPay
https://quizizz.com/api/powerToolsDraw
https://game.quizizz.com/play-api/v2/checkRoom       	{"__cid__":null,"success":false,"error":"API /play-api/v2/ not supported","type":"api.NOT_SUPPORTED"}
https://game.quizizz.com/play-api/v3/       		{"success":false,"error":"Forbidden","type":"api.DEPRECATED"}
https://game.quizizz.com/play-api/v4/       		Still working
https://game.quizizz.com/play-api/v5/       
```

### Private Quiz
```
GET https://quizizz.com/api/main/quiz/60a678e676d452001b6a94a6
GET https://quizizz.com/api/main/quiz/60a678e676d452001b6a94a6?source=join
```

### Shitty get quiz
```
GET https://quizizz.com/api/main/quiz/60a678e676d452001b6a94a6/info
```

### Start game
```
POST https://quizizz.com/api/main/game
content-type: application/json

{
    "quizId":"60a678e676d452001b6a94a6",
    "hostId":"5ec69102f08ab4001bbe762b",
    "type":"live",
    "expiry":7200,
    "locale":"en",
    "gameOptions":{
        "memeset":"5c65cf51a7d584001a2630dd",
        "studentLeaderboard":false,
        "timer":false,
        "timer_3":"off",
        "jumble":true,
        "jumbleAnswers":false,
        "memes":false,
        "showAnswers_2":"never",
        "studentQuizReview_2":"no",
        "showAnswers":false,
        "studentQuizReview":false,
        "limitAttempts":1,
        "studentMusic":false,
        "redemption":"no",
        "powerups":"no",
        "nicknameGenerator":false,
        "loginRequired":true,
        "questionsPerAttempt":0
    },
    "memeSet":"5c65cf51a7d584001a2630dd",
    "groupIds":[],
    "title":null,
    "description":null,
    "assignedTo":[],
    "brandingOptions":null
}
```

### Get game
Returns 400 without teacher cookie. Returns short ID & answers
```
GET https://quizizz.com/api/main/game/60cb64390fa4fb001d53a0ad
Cookie: _sid=v2-10f1428dfd3253717b70811ed226c43e53ae9fcf213998349ff925724cf3585e84bc3e5c80b822eac1c02b410b6b14943bc5933fa2d75b0bf4982f06dc79cdb59581379bdc3f3bcca5daf744ced18c36
```

### Get game without auth
Returns long ID from hash, pin from hash
```
GET https://quizizz.com/api/main/v4/students/game/60cb64390fa4fb001d53a0ad

Worse version:
GET https://quizizz.com/api/main/game/60cb64390fa4fb001d53a0ad/quiz-info
```

### Websocket
```
Socket.io https://socket.quizizz.com/_gsocket/sockUpg
Socket.io https://socket.quizizz.com/_nsocket/sockUpg/socket
```

### Check if pin is valid
Returns long ID, hash, short host ID
```
POST https://game.quizizz.com/play-api/v5/checkRoom
content-type: application/json

{"roomCode":"032231"}
```

### Returns some random quizzes from hash
```
GET https://quizizz.com/api/main/v2/gameSummaryRec?gameId=60cb64390fa4fb001d53a0ad&gameState=waiting
```

### Returns some random quizzes from shortId
```
GET https://quizizz.com/api/main/gameSummaryRec?quizId=60a678e676d452001b6a94a6
GET https://quizizz.com/api/main/quizPageRec?quizId=60a678e676d452001b6a94a6
```

### Get meme set
```
GET https://quizizz.com/api/powerToolsDraw/getMemeSetGame/5c65cf51a7d584001a2630dd
```

### Start game
```
POST https://quizizz.com/api/main/game/start
content-type: application/x-www-form-urlencoded

roomHash=60cb64390fa4fb001d53a0ad
```

### End game
Websocket message
```
socket.emit("getReport", { roomHash: "60cb64390fa4fb001d53a0ad" });
```

### Rejoin game
```
POST https://game.quizizz.com/play-api/v5/rejoinGame
content-type: application/json

{
	"roomHash":"60cb64390fa4fb001d53a0ad",
	"playerId":"Fuzzy Gaming",
	"type":"live",
	"state":"stopped",
	"startSource":"rejoin|gameOver",
	"powerupInternalVersion":"13",
	"soloApis":"v2",
	"mongoId":"603a87abb4e796001b9f6023"
}
```

### Account Available
```
GET https://quizizz.com/user/checkUserEmailAvail?email=charleywright06@gmail.com
GET https://quizizz.com/user/checkUserNameAvail?username=charleywright06
```

### Deeplinks
```
quizizzgame://open/
quizizz://
```

### Misc
Mainly from [https://cf.quizizz.com/assets/v3/j/scripts/js/app_config-networkCalls.9454846550e2f79a69bf.js](https://cf.quizizz.com/assets/v3/j/scripts/js/app_config-networkCalls.9454846550e2f79a69bf.js)
```
POST https://game.quizizz.com/play-api/v4/soloJoin
POST https://game.quizizz.com/play-api/v4/soloProceed
POST https://game.quizizz.com/play-api/v2/soloEnd
GET https://game.quizizz.com/play-api/check
POST https://game.quizizz.com/play-api/v2/update-response
POST https://game.quizizz.com/play-api/v2/update-player-metadata
POST https://game.quizizz.com/play-api/syncPlayerResponses
POST https://game.quizizz.com/play-api/playerGameOver
POST https://game.quizizz.com/play-api/v4/proceedGame
POST https://game.quizizz.com/play-api/getRank
POST https://game.quizizz.com/play-api/v4/getQuestions
POST https://game.quizizz.com/play-api/v5/rejoinGame
POST https://game.quizizz.com/play-api/v5/join
POST https://game.quizizz.com/play-api/v5/checkAssignment
POST https://quizizz.com/api/main/game/60cb796da6f7ee001e52e145/getReport
POST https://quizizz.com/api/main/game/start
POST https://quizizz.com/api/main/game/60cb64390fa4fb001d53a0ad/replay
POST https://game.quizizz.com/play-api/get-team-players

group/add-member
auth/refreshToken
group/token-to-teacher?t=
user/fromtoken
playerProfileV2/quizAttempts?quizId=
user/setAvatar
updateAvatar?avatarId=
v2/getSimilarQuizzes?gameId=
v2/gameSummaryRec?gameId=
v2/playerGameOver
v2/deletePlayer
```

### Grades
```
[
    {
        key: 0,
        value: "Kindergarten",
        wpm: 40,
        age: 5
    }, 
    {
        key: 1,
        value: "1st Grade",
        wpm: 53,
        age: 6
    }, 
    {
        key: 2,
        value: "2nd Grade",
        wpm: 89,
        age: 7
    }, 
    {
        key: 3,
        value: "3rd Grade",
        wpm: 107,
        age: 8
    }, 
    {
        key: 4,
        value: "4th Grade",
        wpm: 123,
        age: 9
    }, 
    {
        key: 5,
        value: "5th Grade",
        wpm: 139,
        age: 10
    }, 
    {
        key: 6,
        value: "6th Grade",
        wpm: 150,
        age: 11
    }, 
    {
        key: 7,
        value: "7th Grade",
        wpm: 150,
        age: 12
    }, 
    {
        key: 8,
        value: "8th Grade",
        wpm: 150,
        age: 13
    }, 
    {
        key: 9,
        value: "9th Grade",
        wpm: 200,
        age: 14
    }, 
    {
        key: 10,
        value: "10th Grade",
        wpm: 200,
        age: 15
    }, 
    {
        key: 11,
        value: "11th Grade",
        wpm: 200,
        age: 16
    }, 
    {
        key: 12,
        value: "12th Grade",
        wpm: 200,
        age: 17
    }, 
    {
        key: 13,
        value: "University",
        wpm: 300,
        age: [18, 24]
    }, 
    {
        key: 14,
        value: "Professional Development",
        wpm: 220,
        age: 25
    }
]
```

### Sources
```
GAME_CODE: {
    _BASE_: "gameCode",
    TYPED: "gameCode|typed",
    PARAM: "gameCode|param",
    PSEUDO_LMS: "gameCode|pseudoLms",
    AFTER_DIALOG: "gameCode|afterDialog",
    AFTER_GROUP_INVITE_ACCEPT: "gameCode|afterGroupInviteAccept"
},
FEATURED: "featured",
SEARCH: "search",
FROM_ADMIN: {
    _BASE_: "fromAdmin",
    PARAM: {
        _BASE_: "fromAdmin|param",
        DIRECT: "fromAdmin|param|direct",
        AFTER_NAME: "fromAdmin|param|afterName",
        SOLO_LINK_SHARE: "fromAdmin|param|soloLinkShare",
        PARENT_EMAIL: "fromAdmin|param|parentEmail",
        PARENT_EMAIL_LINK: "fromAdmin|param|parentEmailLink"
    }
},
LMS: {
    _BASE_: "lms",
    AFTER_PROMPT: "lms|afterPrompt",
    AFTER_GROUP_INVITE_ACCEPT: "lms|afterGroupInviteAccept",
    PRE_GAME_SCREEN_START_ACTION: "lms|preGameScreenStartAction"
},
PRE_GAME_SCREEN: "preGameScreen",
RECONNECT_REJOIN: "reconnectRejoin",
RECENT_ACTIVITY: {
    _BASE_: "recentActivity",
    RUNNING: {
        _BASE_: "recentActivity|running",
        COMPLETE: "recentActivity|running|complete",
        REPLAY: "recentActivity|running|replay",
        PRACTICE: "recentActivity|running|practice",
        START_CHALLENGE_GAME: "recentActivity|running|startChallengeGame"
    },
    COMPLETED: {
        _BASE_: "recentActivity|completed",
        COMPLETE: "recentActivity|completed|complete",
        REPLAY: "recentActivity|completed|replay",
        PRACTICE: "recentActivity|completed|practice",
        START_CHALLENGE_GAME: "recentActivity|completed|startChallengeGame"
    },
    UNREGD_INCOMPLETE: "recentActivity|unregdIncomplete"
},
ACTIVITY: {
    _BASE_: "activity",
    RUNNING: {
        _BASE_: "activity|running",
        COMPLETE: "activity|running|complete",
        REPLAY: "activity|running|replay",
        PRACTICE: "activity|running|practice"
    },
    COMPLETED: {
        _BASE_: "activity|completed",
        COMPLETE: "activity|completed|complete",
        REPLAY: "activity|completed|replay",
        PRACTICE: "activity|completed|practice"
    }
},
REPLAY: {
    _BASE_: "replay",
    SUMMARY: {
        _BASE_: "replay|summary",
        BTN: "replay|summary|btn",
        FLASHCARDS: "replay|summary|flashcards"
    },
    AFTER_AUTH_MODAL: "replay|afterAuthModal",
    REPLAY_LIVE_GAME: "replay|replayLiveGame",
    REPLAY_CHALLENGE_GAME: "replay|replayChallengeGame"
},
REJOIN: {
    _BASE_: "rejoin",
    PARAM: {
        _BASE_: "rejoin|param",
        ROUTE_DATA: "rejoin|param|routeData"
    },
    AUTO: {
        _BASE_: "rejoin|auto",
        WHILE_LMS_FLOW: "rejoin|auto|whileLmsFlow"
    },
    NAVIGATED: {
        _BASE_: "rejoin|navigated",
        WHEN_FORBIDDEN: "rejoin|navigated|whenForbidden"
    },
    GAME_OVER: "rejoin|gameOver"
},
WAITING: {
    _BASE_: "waiting",
    REFRESH: "waiting|refresh"
},
EXISTING_INCOMP_PROMPT: {
    _BASE_: "existingIncompPrompt",
    ON_CHECK_ROOM: "existingIncompPrompt|onCheckRoom",
    ON_JOIN: "existingIncompPrompt|onJoin"
},
RECOMMENDATION: {
    _BASE_: "recommendation",
    FROM_SUMMARY: "recommendation|fromSummary",
    FROM_HOME: "recommendation|fromHome",
    FROM_TOPIC_PAGE: "recommendation|fromTopicPage"
},
GROUP_GAME: {
    _BASE_: "groupGame",
    NOTIFICATION: "groupGame|notification",
    CARD: {
        _BASE_: "groupGame|card",
        RUNNING: "groupGame|card|running",
        RECENT_ACTIVITY: "groupGame|card|recentActivity"
    }
},
FROM_SHARE: {
    _BASE_: "fromShare",
    VIA_ADMIN: "fromShare|viaAdmin"
},
MY_QUIZZES: {
    _BASE_: "myQuizzes",
    FROM_ACTIVITY_PAGE: "myQuizzes|fromActivityPage"
},
CHALLENGE_WAITING: {
    _BASE_: "challengeWaiting"
},
EMBED: "embed"
```
