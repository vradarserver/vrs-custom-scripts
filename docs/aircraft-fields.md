# Aircraft Fields
The **VRS.Aircraft** object exposes a number of fields that carry the state of an aircraft
that is being tracked.

The definitive list of fields is in the source for [aircraft.ts in GitHub](https://github.com/vradarserver/vrs/blob/master/VirtualRadar.WebSite/Site/Web/script/vrs/aircraft.ts). This is
a summary to save people having to wade through the TypeScript to get to the fields.

In the tables of fields below the **Version** column indicates whether the value is present
for both version 2 and 3 (**2+**) or just version 3 (**3**).

If you find any errors or ommissions in this page then please submit a pull request.

## Simple value fields
These are fields that have a standard JavaScript type. The *Type* column indicates the type and
the *Version* indicates whether it 

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|id|`number`|2+|The unique identifier of the aircraft|
|secondsTracked|`number`|2+|The number of seconds that the aircraft has been tracked for|
|updateCounter|`number`|2+|The number of times the aircraft has appeared in an aircraft list refresh|


## `Value<T>` fields
Almost all aircraft fields are of type **`Value<T>`**, where T is either a string, a number, a boolean or an enum type (see below for a list of enum types).

A `Value<T>` has these fields:

|Name|Type|Description|
|----|----|-----------|
|val|`T`|The field's value|
|chg|`boolean`|True if the field's value changed in the latest refresh of the aircraft list|

The *Type* column indicates the T parameter for `Value<T>` - i.e. the type of the *val* field.

So for example, if you have an Aircraft object called *aircraft* and you want to know its ICAO then you
would refer to `aircraft.icao.val` and the result would be a string.

Similarly if you want to know if its altitude changed in the last update then you would test
`aircraft.altitude.chg`.

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|receiverId|`number`|2+|The ID of the receiver that is tracking the aircraft|
|icao|`string`|2+|The aircraft's Mode-S identifier|
|icaoInvalid|`boolean`|2+|True if the ICAO is not valid|
|registration|`string`|2+|The aircraft's registration|
|altitude|`number`|2+|The aircraft's pressure altitude in feet|
|geometricAltitude|`number`|2+|The aircraft's geometric altitude in feet|
|airPressureInHg|`number`|2+|The air pressure in inches of mercury either from the aircraft or from the closest airport|
|altitudeType|`AltitudeType`|2+|The type of altitude transmitted by the aircraft|
|targetAltitude|`number`|2+|The target altitude set on the auto-pilot (ADSB-2+ only)|
|callsign|`string`|2+|The callsign|
|callsignSuspect|`boolean`|2+|True if the callsign was retrieved from a message type that is open to misinterpretation|
|latitude|`number`|2+|The latitude portion of the aircraft's position|
|longitude|`number`|2+|The latitude portion of the aircraft's position|
|isMlat|`boolean`|2+|True if the position was calculated by MLAT|
|positionAgeSeconds|`number`|3|The number of seconds that have elapsed since the aircraft last sent a position|
|positionTime|`number`|2+|The time the position was reported by the aircraft as Date ticks|
|positionStale|`boolean`|2+|True if the position is older than the display threshold|
|speed|`number`|2+|The ground speed of the aircraft in knots|
|speedType|`SpeedType`|2+|The type of speed transmitted by the aircraft|
|verticalSpeed|`number`|2+|The vertical speed of the aircraft in feet per minute|
|verticalSpeedType|`AltitudeType`|2+|The type of vertical speed transmitted by the aircraft|
|heading|`number`|2+|The track across the ground of the aircraft in degrees where 0 = true north|
|headingIsTrue|`boolean`|2+|True if *heading* is true north rather than magnetic north|
|targetHeading|`number`|2+|The desired heading held by the autopilot (ADSB-2+ only)|
|manufacturer|`string`|2+|The aircraft manufacturer|
|serial|`string`|2+|The aircraft's serial number|
|yearBuilt|`string`|2+|The year the aircraft was built|
|model|`string`|2+|The aircraft model|
|modelIcao|`string`|2+|The aircraft model's ICAO 8640 code|
|from|`RouteValue`|2+|The starting airport in the aircraft's route|
|to|`RouteValue`|2+|The final airport in the aircraft's route|
|via|`ArrayValue<RouteValue>`|2+|The airports between *from* and *to* in the aircraft's route|
|isCharterFlight|`boolean`|3|True if the callsign indicates that this is a charter flight and so does not have a route|
|isPositioningFlight|`boolean`|3|True if the callsign indicates that this is a positioning or ferry flight and so does not have a route|
|operator|`string`|2+|The person or corporation that operates the aircraft|
|operatorIcao|`string`|2+|The ICAO of the corporation that operates the aircraft|
|squawk|`string`|2+|The squawk code being transmitted by the aircraft|
|identActiveidentActive|`boolean`|3|True if the aircraft is transmitting ident|
|isEmergency|`boolean`|2+|True if *squawk* represents an emergency squawk code|
|distanceFromHereKm|`number`|2+|The distance from the browser location to the aircraft in kilometres|
|bearingFromHere|`number`|2+|The bearing from true north to the browser location to the aircraft|
|wakeTurbulenceCat|`WakeTurbulenceCategory`|2+|The aircraft's wake turbulence category|
|countEngines|`string`|2+|The number of engines on the aircraft (note this is a string)|
|engineType|`EngineType`|2+|The type of the main engines on the aircraft|
|enginePlacement|`EnginePlacement`|2+|The type of the main engines on the aircraft|
|species|`Species`|2+|The type of aircraft, e.g. helicopter, fixed wing etc.|
|isMilitary|`boolean`|2+|True if the aircraft is operated by a military force|
|isTisb|`boolean`|2+|True if the aircraft details were transmitted over TISB|
|country|`string`|2+|The country of registration|
|hasPicture|`boolean`|2+|True if the server has a local picture of the aircraft|
|pictureWidth|`number`|2+|The local picture width in pixels|
|pictureHeight|`number`|2+|The local picture height in pixels|
|countFlights|`number`|2+|The number of flight records for this aircraft in *BaseStation.sqb*|
|countMessages|`number`|2+|The number of messages picked up for this aircraft in the current tracking session|
|isOnGround|`boolean`|2+|True if the aircraft is indicating that it is not flying|
|userTag|`string`|2+|The value of the UserTag field from *BaseStation.sqb*|
|userInterested|`boolean`|2+|The value of the Interested field from *BaseStation.sqb*|
|signalLevel|`number`|2+|The signal level of the last message transmitted by the aircraft|
|averageSignalLevel|`number`|2+|The average signal level over all messages transmitted by the aircraft|
|airportDataThumbnails|`AirportDataThumbnails`|2+|An object describing the thumbnails for the aircraft on airportdata.com|
|transponderType|`TransponderType`|2+|The type of transponder equipped by the aircraft|
|shortTrail|`ArrayValue<ShortTrailValue>`|2+|The coordinates for the aircraft's short trail|
|fullTrail|`ArrayValue<FullTrailValue>`|2+|The coordinates for the aircraft's full trail|

## `ArrayValue<T>`

Fields that hold a collection of trail coordinates are of type **`ArrayValue<T>`** where T is the type of the object being stored.

If the array changes in an aircraft list refresh then the code will trim objects from the start of the
array and add new objects to the end of the array.

An `ArrayValue<T>` has these fields:

|Name|Type|Description|
|----|----|-----------|
|arr|T[]|The array of values|
|chg|boolean|True if any element in *arr* changed in the last refresh of the aircraft list|
|chgIdx|number|The index of the first value added in the last update, -1 if no fields were added|
|trimStartCount|number|The number of array elements that were removed from the start of the array in the last update|

## Enum Types

These are described in Enum.ts. You can use the named values in your JavaScript, e.g.:

`aircraft.species.val === Species.Helicopter;`

### AltitudeType

All values are of type `number`:

- Barometric
- Geometric

### EnginePlacement

All values are of type `number`:

- Unknown
- AftMounted
- WingBuried
- FuselageBuried
- NoseMounted
- WingMounted

### EngineType

All values are of type `number`:

- None
- Piston
- Turbo
- Jet
- Electric
- Rocket

### Species

All values are of type `number`:

- None
- LandPlane
- SeaPlane
- Amphibian
- Helicopter
- Gyrocopter
- Tiltwing
- GroundVehicle
- Tower

### SpeedType

All values are of type `string`:

- Knots
- MilesPerHour
- KilometresPerHour

### TransponderType

All values are of type `number`:

- Unknown
- ModeS
- Adsbversion
- Adsb0
- Adsb1
- Adsb2

### WakeTurbulenceCategory

All values are of type `number`:

- None
- Light
- Medium
- Heavy

## Object Value Types

### AirportDataThumbnails

An object that describes the thumbnails available for the aircraft on airportdata.com.

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|status|`number`|2+|The HTTP status code returned from airportdata.com when requesting thumbnails|
|error|`string`|2+|The error message (if any) returned from airportdata.com when requesting thumbnails|
|data|`AirportDataThumbnail[]`|2+|An array of thumbnail objects|

The **AirportDataThumbnail** object has the following fields:

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|image|`string`|2+|The URL to the thumbnail|
|link|`string`|2+|The URL to the full-sized image|
|photographer|`string`|2+|The name of the photographer for the copyright notice|

### ShortTrailValue

Describes a coordinate in a short trail. Short trails are only sent if they have been
requested by the user.

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|lat|`number`|2+|The latitude of the coordinate|
|lat|`number`|2+|The longitude of the coordinate|
|posnTick|`number`|2+|The JavaScript tick time at which the position was recorded|
|altitude|`number`|2+|The altitude in feet when the position was recorded|
|speed|`number`|2+|The ground speed in knots when the position was recorded|

### FullTrailValue

Describes a coordinate in a full trail. Full trails are only sent if they have been
requested by the user.

|Name|Type|Version|Description|
|----|----|:-----:|-----------|
|lat|`number`|2+|The latitude of the coordinate|
|lat|`number`|2+|The longitude of the coordinate|
|heading|`number`|2+|The heading of the aircraft when the position was recorded|
|altitude|`number`|2+|The altitude in feet when the position was recorded|
|speed|`number`|2+|The ground speed in knots when the position was recorded|
|chg|`boolean`|2+|True if this modifies the previous last element of the array to supply a new *lat* and *lng*|

Full trails only send new positions when the heading, altitude or speed changes. If only the position
changes then the existing trail is extended to the new position and *chg* gets set to indicate that it
is just a position update.

### RouteValue

This extends `Value<string>` to add a new function called **getAirportCode** that extracts and returns
the airport's code from the airport description.

Otherwise the string is both the airport code and its description.
