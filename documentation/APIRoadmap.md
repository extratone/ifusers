# Infinite Flight API Roadmap
Updated `01032023-125209`

- [**GitHub Issue**](https://github.com/extratone/ifusers/issues/5)
- [Source](https://trello.com/b/8ZoaVL6c/api-wishlist)
- [Shared iCloud Numbers Spreadsheet](https://www.icloud.com/numbers/0beOSIEUB_pzz6Dy1IS4gKwVw#API_Wishlist)
- [Shared Apple Note](https://www.icloud.com/notes/0fereEAFOAARD6dsgF-_nMtOQ#Infinite_Flight_API_Wishlist)
- [WTF](https://davidblue.wtf/drafts/F07F8318-C4C1-4B35-8FC1-4310306B5D90.html)]
- [WTF Shortlink](https://davidblue.wtf/ifroadmap) - `https://davidblue.wtf/ifroadmap`
- [Local](shareddocuments:///private/var/mobile/Library/Mobile%20Documents/com~apple~CloudDocs/Written/F07F8318-C4C1-4B35-8FC1-4310306B5D90.md)
- [Craft Local](craftdocs://open?blockId=1F312E55-6231-4C9A-A20F-FC60F243C986&spaceId=db0fc03f-3fc9-3575-cb0a-e492d5f5204c)
- [Craft Publish](https://www.craft.do/s/HyikSfjadZq0E9)
- [Simplenote Local](simplenote://note/b506e551f45f47be844af0711b575d8d)
- [Simplenote Publish](http://simp.ly/publish/myn5YR)
- [Draft](drafts://open?uuid=F07F8318-C4C1-4B35-8FC1-4310306B5D90)
- [Telegraph](https://telegra.ph/Infinite-Flight-API-Roadmap-01-03)
- [Things](things:///show?id=5UY9PhoFcw28JaDDQq3X3T)

---

[![Infinite Flight API Wishlist Trello Board](https://www.davidblue.bio/uploads/2023/45c3d11dc3.png)](https://trello.com/b/8ZoaVL6c/api-wishlist)

#### commands/reversethrust
Last Updated `12292022-210153`

- [**URL**](https://trello.com/c/6qaFOucs/2-commands-reversethrust)

this command doesn't appear to work (tested with no argument Int32, boolean, json structured identical to APIv1)
#### A bug!
Last Updated `04022020-151838`

- [**URL**](https://trello.com/c/Q2fWZuJh/1-a-bug)


#### commands/reversethrust
Last Updated `04022020-152543`

- [**URL**](https://trello.com/c/uYjhP7qj/3-commands-reversethrust)


#### Get Flight Plan - Sending 0.0 lat/lng instead of null (see description)
Last Updated `07232022-184220`

- [**URL**](https://trello.com/c/4EQF6eBL/54-get-flight-plan-sending-00-lat-lng-instead-of-null-see-description)

**0 is something. Null is nothing.**

A null coordinate should be the proper way to tell if the API server had found **nothing**. A zero coordinate can be interpreted as valid (such as latitudes along the equator).
#### Live API Docs doesn't appropriately mention ALL nullable values (see description)
Last Updated `07152022-191541`

- [**URL**](https://trello.com/c/1EVm5lHb/50-live-api-docs-doesnt-appropriately-mention-all-nullable-values-see-description)

It would also be better to mention if they can be null in the "Type" column and in the "Description" if there's any additional info.

This makes the API somewhat unpredictable. For example in the v2/sessions/{sessionId}/flights endpoint the username can be null (not empty string) if the user is anonymous. Then it is reasonable to assume that v2/sessions/{sessionId}/atc will also send back a null for the username (if needs be). But that is not the case. The API can send a non-empty string with a "fake" username for presentation ("Controller").

Complete list of what I could get :

v2/users :
UserStats - discourseUsername
UserStats - virtualOrganization

v2/sessions/{sessionId}/atc :
ActiveATCFacility - username
ActiveATCFacility - virtualOrganization
ActiveATCFacility - airportName

v2/users/{userId}/atc/{atcSessionId} :
ATCFacility - airportIcao

v2/sessions/{sessionId}/flights :
FlightEntry - virtualOrganization
FlightEntry - username

v2/sessions/{sessionId}/flights/{flightId}/flightplan :
FlightPlanItem - name
FlightPlanItem - children
FlightPlanItem - identifier

v2/tracks :
OceanicTrack - eastLevels
OceanicTrack - westLevels

v2/users/{userId}/flights & v2/users/{userId}/atc :
PaginatedList - data

v2/users/{userId}/flights & v2/users/{userId}/flights/{flightId} :
UserFlight - liveryId (mentioned in another issue)
UserFlight - callsign

v2/sessions/{sessionId}/notams :
NotamResult - sessionId
#### simulator/throttle set and get are negative if each other
Last Updated `09062022-235051`

- [**URL**](https://trello.com/c/new6S2W4/68-simulator-throttle-set-and-get-are-negative-if-each-other)

If you set simulator/throttle to a value x, then request the value and get a value y, y = -x. 

Set value of simulator/throttle: 100
Get value of simulator/throttle: -100
#### Features Endpoint
Last Updated `12162022-223920`

- [**URL**](https://trello.com/c/TnmEMG7d/74-features-endpoint)

TlL;DR: An `aircraft/0/features/*` endpoint would allow apps to see what capabilities an aircraft has. E.g.: `aircraft/0/features/retractable_gear : True` and `aircraft/0/features/spoilers : False` for the TBM. 



This is a little more abstract. It’s impossible to tell what capabilities an aircraft has right now. The C172 doesn’t have an endpoint for the Boeing MFD, but it does have endpoints for things like spoilers, auto brakes, and even carrier ops. 

I’d like to be able to implement some conditional logic, e.g. only show options for carrier ops if the current aircraft has a tail hook. Obviously this can be worked around by hardcoding a tail hook option to be available for the F-18… but it becomes frustrating to hardcode whether every aircraft in the fleet has spoilers, auto brakes, reverse thrust, retractable gear, etc. This option is also not future-proof, as any future aircraft would need a configuration defined in the third-party app. 

I suggest the creation of `aircraft/0/features/*` endpoints for all these features that vary by aircraft. 

An alternative option would be to remove all these endpoints for aircraft they don’t apply to. No need for the C172 to have a carrier ops endpoint exposed to me.
#### Get User Flights - add violations received during flight
Last Updated `11082022-115759`

- [**URL**](https://trello.com/c/7s9Z0oWj/71-get-user-flights-add-violations-received-during-flight)


#### Kafka Topic or any producer for IF events
Last Updated `01032023-111114`

- [**URL**](https://trello.com/c/5LZImpqN/48-kafka-topic-or-any-producer-for-if-events)

https://community.infiniteflight.com/t/request-suggestion-a-kafka-topic-or-a-subscribable-stream-for-if-events/675603
#### Add a command to Connect v2 API comparable to "NetworkJoystick.SetNetworkJoystickAxes" in the v1 API
Last Updated `04192022-120856`

- [**URL**](https://trello.com/c/8X5cIXXg/44-add-a-command-to-connect-v2-api-comparable-to-networkjoysticksetnetworkjoystickaxes-in-the-v1-api)


#### provide a better error response
Last Updated `10022020-233716`

- [**URL**](https://trello.com/c/IzpDdt2W/15-provide-a-better-error-response)

Currently the api returns OK (Result = 0) with a TextRespones indicating error. Would be nice to either have it return erorr, or return an error type, so it is easier to understand when invalid data has been sent
#### simulator/throttle/reverse
Last Updated `04022020-154731`

- [**URL**](https://trello.com/c/SVNDVLUU/8-simulator-throttle-reverse)

a get and set boolean state, in order to set reverse thrust on and off, e.g. setState(ID: "sim/throttle/reverse", value: true) to activate reverse thrust
#### generic ATC command
Last Updated `04022020-162119`

- [**URL**](https://trello.com/c/870YvUD7/9-generic-atc-command)

Right now there's 10 separate ATC commands, no more, this makes it impossible to send higher values through the api. Something like RunCommand(ID: "atcCommand", value: 12) which would send the ID of the ATC command, would help
#### add infiniteflight/commands when on the menu (infiniteflight/appstate and others are available in the sim, but not from the menu)
Last Updated `06052020-230003`

- [**URL**](https://trello.com/c/NRYWH6CW/18-add-infiniteflight-commands-when-on-the-menu-infiniteflight-appstate-and-others-are-available-in-the-sim-but-not-from-the-menu)


#### commands/togglemap
Last Updated `08212020-205123`

- [**URL**](https://trello.com/c/jhJtW2A9/19-commands-togglemap)

No way to show the map atm. Would be nice to have this, as well as zoom/motion and a state like mapIsShowing or something
#### AirportDetails Endpoint for Live API
Last Updated `10032020-013723`

- [**URL**](https://trello.com/c/jcCT7pWm/23-airportdetails-endpoint-for-live-api)

Requested by Chris_S via IFC. See https://community.infiniteflight.com/t/new-api-airportdetails-aspx-request/417143.
#### Select Aircraft as Controller in Connect API
Last Updated `08282020-213045`

- [**URL**](https://trello.com/c/Me51efBe/25-select-aircraft-as-controller-in-connect-api)

As an ATC, you can currently send certain commands based on their number. However, you cannot select an aircraft to send them to. See https://community.infiniteflight.com/t/select-aircraft-in-atc-interface/417256/2.
#### No way to tell if an aircraft has beacon (or other) lights. 
Last Updated `12162022-050111`

- [**URL**](https://trello.com/c/yL9gYxZd/72-no-way-to-tell-if-an-aircraft-has-beacon-or-other-lights)

Not all aircraft have beacon lights (TBM, A-10). There’s no difference in the api in this case -- there are still all the same endpoints. This is expandable in case an aircraft with less lights (e.g. a J-3 Cub) is added. Endpoints such as `aircraft/0/has_beacon lights` for all the different lights would be helpful. 
#### Way to return current camera from ConnectAPI
Last Updated `08092022-125203`

- [**URL**](https://trello.com/c/ka86LNzx/26-way-to-return-current-camera-from-connectapi)

The api gives info on different cameras by number (I can look up the name of camera 4, for example) but there’s no way to find out the number of the current camera. 
#### Ability to set time and date
Last Updated `01222021-060642`

- [**URL**](https://trello.com/c/k21sWzRQ/30-ability-to-set-time-and-date)


#### UDP connections for flight control axes
Last Updated `03092022-184242`

- [**URL**](https://trello.com/c/suHDLiGM/36-udp-connections-for-flight-control-axes)

UDP connection would allow for better latency of flight control commands. Sending camera commands via the UDP SmoothTrack API is faster than sending them over TCP. I’d like to be able to continuously send flight control commands the same way. 
#### aircraft/0/weight
Last Updated `03312022-142754`

- [**URL**](https://trello.com/c/ZNrf10bD/37-aircraft-0-weight)


#### aircraft/0/mlw
Last Updated `03312022-142757`

- [**URL**](https://trello.com/c/8FsTQ0dc/38-aircraft-0-mlw)


#### aircraft/0/mtow
Last Updated `03312022-142800`

- [**URL**](https://trello.com/c/8zleI1BG/39-aircraft-0-mtow)


#### Opening up the Connect API for ATC
Last Updated `04112022-063130`

- [**URL**](https://trello.com/c/SHJx89rA/40-opening-up-the-connect-api-for-atc)


#### Get Airport Status & Get World Status - Proper airportName field (completely distinct from airportIcao) with the full name in Infinite Flight of the airport (e.g EGLL / London Heathrow)
Last Updated `04142022-060922`

- [**URL**](https://trello.com/c/gYbDkjUs/42-get-airport-status-get-world-status-proper-airportname-field-completely-distinct-from-airporticao-with-the-full-name-in-infinite)


#### Include a user's roles in the flights endpoint
Last Updated `04232022-054817`

- [**URL**](https://trello.com/c/xet6HSeM/46-include-a-users-roles-in-the-flights-endpoint)


#### The API responses being compatible in multiple languages.
Last Updated `06042022-231022`

- [**URL**](https://trello.com/c/Ob1NHA8R/53-the-api-responses-being-compatible-in-multiple-languages)

Some people in our development may not understand english well. For example, the json responses will appear in another language like french. As apart of this, add endpoints which allows users to change the language of their data. for example: /v2/sessions?apikey={apikey}&lang=cn (for chinese) or /v2/sessions?apikey={apikey}&lang=de (for german)
#### I accidentally created a new card, please delete this one.
Last Updated `06042022-231040`

- [**URL**](https://trello.com/c/zDx8kHNh/52-i-accidentally-created-a-new-card-please-delete-this-one)


#### Search userIds with username regex expression
Last Updated `07152022-161043`

- [**URL**](https://trello.com/c/j5uuW8Q4/55-search-userids-with-username-regex-expression)


#### Infinite Flight OAuth system (@see description)
Last Updated `07162022-062209`

- [**URL**](https://trello.com/c/dfmUXRmX/56-infinite-flight-oauth-system-see-description)

Similar to Sign in with Google. Users can sign in using their Infinite Flight account. The API would expose their discourse username, email and profile picture. 

It would be especially useful when syncing up their IF account to a third party app (in the easiest way possible).
#### Get a list of userIds by role
Last Updated `07162022-062343`

- [**URL**](https://trello.com/c/0VwfsEcU/57-get-a-list-of-userids-by-role)

Get a list of userIds of specific groups such as IFATCs / mods / staff / other....
#### Get Flights - Active / Away status
Last Updated `07162022-113751`

- [**URL**](https://trello.com/c/z8v4QHmf/58-get-flights-active-away-status)


#### Get User Stats (HTTP POST) - Number of online ATC sessions (we have onlineFlights for flights)
Last Updated `07172022-110411`

- [**URL**](https://trello.com/c/v8y2XCtt/59-get-user-stats-http-post-number-of-online-atc-sessions-we-have-onlineflights-for-flights)


#### Get User ATC Session(s) - Number of violations issued
Last Updated `07192022-065147`

- [**URL**](https://trello.com/c/MvXa4aUL/60-get-user-atc-sessions-number-of-violations-issued)


#### Get User ATC Session(s) - Server name
Last Updated `07192022-065243`

- [**URL**](https://trello.com/c/tmFKGDcp/61-get-user-atc-sessions-server-name)


#### Get Flights - Time last updated & possibly refresh delay in sec/min between updates. Helps to perfectly sync with IF (example useful case: stops the flights from getting thrown backwards when animating them)
Last Updated `07212022-124031`

- [**URL**](https://trello.com/c/vAQ6yZqZ/62-get-flights-time-last-updated-possibly-refresh-delay-in-sec-min-between-updates-helps-to-perfectly-sync-with-if-example-useful-c)


#### Ability to access functions of the editor
Last Updated `07282022-135054`

- [**URL**](https://trello.com/c/5ogZkyWx/63-ability-to-access-functions-of-the-editor)

It would be cool to have access to different scenery editor functions via the connect API. Such as placing, modifying, deleting, etc. 

The only one that I currently know of is the delete command. Even that still prompts the user to confirm though.
#### Get Session Detail - Fetch grade/other requirements (Get Sessions returns only if restricted or not)
Last Updated `08182022-075138`

- [**URL**](https://trello.com/c/waIXBaVC/64-get-session-detail-fetch-grade-other-requirements-get-sessions-returns-only-if-restricted-or-not)


#### Get information about surrounding traffic in Connect V2
Last Updated `08202022-211418`

- [**URL**](https://trello.com/c/rsFEpNHt/65-get-information-about-surrounding-traffic-in-connect-v2)


#### Get User Detail / Post User Stats - Number of online ATC sessions
Last Updated `08262022-162945`

- [**URL**](https://trello.com/c/nd9IVOut/66-get-user-detail-post-user-stats-number-of-online-atc-sessions)


#### Get User Detail / Post User Stats - Total time ATC Sessions
Last Updated `08262022-162950`

- [**URL**](https://trello.com/c/O628Rnkc/67-get-user-detail-post-user-stats-total-time-atc-sessions)


#### Get ATC Schedule
Last Updated `09062022-105631`

- [**URL**](https://trello.com/c/v8r5AE4n/69-get-atc-schedule)


#### aircraft/0/systems/nav_lights_switch endpoint is missing
Last Updated `12292022-212806`

- [**URL**](https://trello.com/c/VmmEfp7i/73-aircraft-0-systems-navlightsswitch-endpoint-is-missing)

This endpoint exists for the other three types of lights. It’s nice because it takes a boolean rather than a 1 or 0 int. 

A workaround is to use aircraft/0/systems/electrical_switch/nav_lights_switch/state. 
#### aircraft/0/systems/autopilot/on
Last Updated `09112020-085058`

- [**URL**](https://trello.com/c/1rmeBMkE/12-aircraft-0-systems-autopilot-on)

This does not have setState functionality. Tested with Bools
#### Set State - Boolean - Instantaneous gear descend/retract : aircraft/0/systems/landing_gear/lever_state
Last Updated `12292022-210801`

- [**URL**](https://trello.com/c/pApxxkFz/43-set-state-boolean-instantaneous-gear-descend-retract-aircraft-0-systems-landinggear-leverstate)


#### commands/Engine.Start and commands/Engine.Stop
Last Updated `12292022-210208`

- [**URL**](https://trello.com/c/EMlP81nQ/7-commands-enginestart-and-commands-enginestop)

These do not function. Tested with engine numbers as an argument
#### Endpoint GET - v2/users/{userId}/flights returning systematically null values for the liveryId [FIX IN PROGRESS]
Last Updated `12162022-045130`

- [**URL**](https://trello.com/c/TaguC35s/49-endpoint-get-v2-users-userid-flights-returning-systematically-null-values-for-the-liveryid-fix-in-progress)

It seems that the liveryId returns a correct value for some people such as KaiM & Laura but for most people it seems that it doesn't.

#### aircraft/0/systems/autopilot/spd/target
Last Updated `01032023-110950`

- [**URL**](https://trello.com/c/LK6zabWe/4-aircraft-0-systems-autopilot-spd-target)

setState does not change the value of the autopilot spd target. Tested with float value.
#### ATC Actions for non-IFATC and Time Periods
Last Updated `10022020-140829`

- [**URL**](https://trello.com/c/pOH2YUXh/22-atc-actions-for-non-ifatc-and-time-periods)

In Live API UserDetails endpoint. Request by Chris_S via IFC. See https://community.infiniteflight.com/t/userdetails-aspx-request/416101.
#### commands/resetcamera
Last Updated `05212021-213339`

- [**URL**](https://trello.com/c/DvBNZWWI/6-commands-resetcamera)

A command like this to recenter the camera (like on double tap) would be useful
#### Missing proper documentation
Last Updated `10042020-234941`

- [**URL**](https://trello.com/c/KIwe3BuT/14-missing-proper-documentation)

https://github.com/flyingdevelopmentstudio/infiniteflight-api
Made by @philippe and @Nicholas. Great starting point and very helpful but outdated (? perhaps) and uncomplete. 

#### GetUserStats - Level 2/3 Count
Last Updated `01062021-130336`

- [**URL**](https://trello.com/c/Y845xy2b/29-getuserstats-level-2-3-count)

Add Level 2/3 count for 24 hours to the GetUserStats endpoint similar to the old api with the 24 hour ghosting. This will save going to the grade endpoint. 
#### Atlantic / pacific tracks
Last Updated `02022021-152546`

- [**URL**](https://trello.com/c/6W3QALYx/27-atlantic-pacific-tracks)

It would be great to be able to fetch the current tracks from infinite flight. This could also include the new tracks that Misha has been testing.
#### Historical Data for Live API
Last Updated `02032022-035219`

- [**URL**](https://trello.com/c/9mv6zaBD/5-historical-data-for-live-api)

See https://community.infiniteflight.com/t/historical-flights-in-userdetails-aspx/417261/2
#### NOTAMS / TFR(s)
Last Updated `02122022-172702`

- [**URL**](https://trello.com/c/bgDeXrpl/10-notams-tfrs)

Be able to receive the current TFRs through the API.
#### Get ATC operations gained from a particular controlling session
Last Updated `02122022-172704`

- [**URL**](https://trello.com/c/9cZLs4dD/31-get-atc-operations-gained-from-a-particular-controlling-session)


#### Live API Airport Details Endpoint
Last Updated `03282022-035349`

- [**URL**](https://trello.com/c/PaJU84Te/24-live-api-airport-details-endpoint)

See https://community.infiniteflight.com/t/new-api-airportdetails-aspx-request/417143.
#### Add a state in the Connect v2 API to interrogate (and set) the rudder brakes.
Last Updated `12032022-232115`

- [**URL**](https://trello.com/c/EGg2ogIQ/45-add-a-state-in-the-connect-v2-api-to-interrogate-and-set-the-rudder-brakes)

`aircraft/0/systems/brakes/left/percentage`
#### axis for dynamic braking
Last Updated `12032022-232134`

- [**URL**](https://trello.com/c/TBH1RHCe/11-axis-for-dynamic-braking)

this has been added! `aircraft/0/systems/brakes/left/percentage`, and the right side too
#### Elevator trim direct setting state
Last Updated `12032022-232226`

- [**URL**](https://trello.com/c/6mHwjjQr/17-elevator-trim-direct-setting-state)

available as: aircraft/0/systems/axes/elevator_trim
#### Flight time and range for current flight
Last Updated `01062021-130332`

- [**URL**](https://trello.com/c/aOQKrOSg/28-flight-time-and-range-for-current-flight)


#### commands/Pushback only attaches/detaches tug but doesn’t push back
Last Updated `12292022-212702`

- [**URL**](https://trello.com/c/QuvGDKl0/47-commands-pushback-only-attaches-detaches-tug-but-doesnt-push-back)


#### provide V1 api Command.SetGearState
Last Updated `05212021-213343`

- [**URL**](https://trello.com/c/bfhvVsEw/16-provide-v1-api-commandsetgearstate)

I know it is old API, but would be a huge improvement Currently you can only toggle gear, so setting the gear to a specific state requires another query to the aircraft state
#### Request multiple flight plans through single request
Last Updated `02032022-044221`

- [**URL**](https://trello.com/c/CSpNQZmc/32-request-multiple-flight-plans-through-single-request)

A system for getting multiple flight plans all at once, similar to the current system for getting user information.
#### Ability to Generate API Keys
Last Updated `02032022-044251`

- [**URL**](https://trello.com/c/Tiee6ZP0/21-ability-to-generate-api-keys)

Possibly through a developer center, anyone could be able to get their own API Key. Could be done through a review and approve workflow.
#### Get User Stats - Add a serverId query parameter which will fetch the stats of all pilots & ATC in the server in addition with the userIds provided in the body of the POST request
Last Updated `05252022-192208`

- [**URL**](https://trello.com/c/kw8WnoVA/41-get-user-stats-add-a-serverid-query-parameter-which-will-fetch-the-stats-of-all-pilots-atc-in-the-server-in-addition-with-the-us)


#### Webhooks/Event Subscriptions
Last Updated `02032022-044253`

- [**URL**](https://trello.com/c/LLfrX6Zc/20-webhooks-event-subscriptions)

Implement a "don't call us, we'll call you" system for some events in the Live API. Possible events:
- Certain User Opened ATC Facility
- Certain User Begins Flight
- Certain User Closed ATC Facility
- Certain User Ends Flight
#### Multiple flight ids for flight plan endpoint.
Last Updated `04082022-204752`

- [**URL**](https://trello.com/c/keEvzy9W/34-multiple-flight-ids-for-flight-plan-endpoint)

 Example: https://api.infiniteflight.com/public/v2/flight//flightplan?id=12312541&id=9877835&id=219873

Should be able to fetch an array of flight plans for multiple users

Original Request in IFC: https://community.infiniteflight.com/t/feature-request-accept-multiple-flight-ids-for-get-flight-plan-endpoint/653702
#### Request Multiple FPLs (Link to IFC)
Last Updated `04082022-204754`

- [**URL**](https://trello.com/c/mMTuyJS7/35-request-multiple-fpls-link-to-ifc)

This would be useful for getting ETAs for a list of flights, for example: flights inbound to an airport.

More info below:
https://community.infiniteflight.com/t/feature-request-accept-multiple-flight-ids-for-get-flight-plan-endpoint/653702/20

#### Get flight plan by IFC Name
Last Updated `04082022-204812`

- [**URL**](https://trello.com/c/JxA786Qs/33-get-flight-plan-by-ifc-name)


#### Get All Liveries - Include aircraft registration
Last Updated `09282022-060832`

- [**URL**](https://trello.com/c/OT4MD7GF/70-get-all-liveries-include-aircraft-registration)

We don't record this data and won't be adding this at this time. Sorry!