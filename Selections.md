# API

## General
<a name="recast.settings" href="API#recast.settings">#</a> recast.<b>settings</b>(<i>options</i>)

Apply new navigation mesh settings. It is required to `build()` the navmesh to have them applied.<br>
Supported options are:
* cellSize : 
* cellHeight
* agentHeight : Reference agent height
* agentRadius : Reference agent radius
* agentMaxClimb : Maximum height an agent can climb
* agentMaxSlope : Maximum slope an agent can use, in degrees
* regionMinSize : Minimum size of a region to consider
* regionMergeSize : Minimum size of a region before merging to the nearest one
* edgeMaxLen : Maximum edge length 
* edgeMaxError : ...
* vertsPerPoly : ...
* detailSampleDist : ...
* detailSampleMaxError : ...


<a name="recast.OBJLoader" href="API#recast.OBJLoader">#</a> recast.<b>OBJLoader</b>(<i>path or url</i>)

Load an `.obj` file by its path. It uses `fs.readFile()` in Node and an `XmlHttpRequest` in the browser.

<a name="recast.OBJDataLoader" href="API#recast.OBJDataLoader">#</a> recast.<b>OBJDataLoader</b>(<i>OBJ contents as string</i>)

Load an `OBJ` directly with its content. Useful in some cases when you want to manage geometries on your own.

<a name="recast.buildSolo" href="API#recast.buildSolo">#</a> recast.<b>buildSolo</b>(<i>callback</i>)

Build a single-object navigation mesh. It's generally slower to generate than a tiled navmesh and faster to update, but disable some features like temporary obstacles (unlikely to change limitation).

<a name="recast.buildTiled" href="API#recast.buildTiled">#</a> recast.<b>buildTiled</b>(<i>callback</i>)

Build a tiled navigation mesh. It's generally faster to generate than a solo navmesh and slower to update, but disable some features like off-mesh connections (current limitation, likely to be enabled in the future).

## Basic navmesh operations
<a name="recast.getRandomPoint" href="API#recast.getRandomPoint">#</a> recast.<b>getRandomPoint</b>(<i>callback</i>)

Get a random navigable position. `callback` is called with 3 arguments `x`, `y`, and `z`.

<a name="recast.findNearestPoint" href="API#recast.findNearestPoint">#</a> recast.<b>findNearestPoint</b>(<i>float near_x</i>, <i>float near_y</i>, <i>float near_z</i>, <i>float extend_x</i>, <i>float extend_y</i>, <i>float extend_z</i>, <i>callback</i>)

Find the nearest navigable point. `callback` is called with 3 arguments `x`, `y`, and `z`.

<a name="recast.findNearestPoly" href="API#recast.findNearestPoly">#</a> recast.<b>findNearestPoly</b>(<i>float near_x</i>, <i>float near_y</i>, <i>float near_z</i>, <i>float extend_x</i>, <i>float extend_y</i>, <i>float extend_z</i>, <i>callback</i>)

Find the nearest navigable polygon. `callback` is called with 1 argument `polygon`.

    callback(polygon) {
        polygon.ref      // the polygon_id,
        polygon.vertices // array of vertices
    }

<a name="recast.queryPolygons" href="API#recast.queryPolygons">#</a> recast.<b>queryPolygons</b>(<i>float near_x</i>, <i>float near_y</i>, <i>float near_z</i>, <i>float extend_x</i>, <i>float extend_y</i>, <i>float extend_z</i>, <i>max</i>, <i>callback</i>)

Find all or up to `max` nearest polygons from `near` point. `callback` is called with 1 argument: an array of polygons.

    callback(polygons) {
        polygon[0].ref      // the polygon_id,
        polygon[0].vertices // array of vertices
    }

<a name="recast.setPolyFlags" href="API#recast.setPolyFlags">#</a> recast.<b>setPolyFlags</b>(<i>float near_x</i>, <i>float near_y</i>, <i>float near_z</i>, <i>float extend_x</i>, <i>float extend_y</i>, <i>float extend_z</i>, <i>bitmask flags</i>)

Set flags on nearest polygons from `near` point.

<a name="recast.setPolyFlagsByRef" href="API#recast.setPolyFlagsByRef">#</a> recast.<b>setPolyFlagsByRef</b>(<i>polygon_id</i>, <i>bitmask flags</i>)

Set flags on a single polygon.

<a name="recast.findPath" href="API#recast.findPath">#</a> recast.<b>findPath</b>(<i>float from_x</i>, <i>float from_y</i>, <i>float from_z</i>, <i>float to_x</i>, <i>float to_y</i>, <i>float to_z</i>, <i>int max</i>, <i>callback</i>)

Find a all - or up to `max` - `waypoints` points between two points. `callback` is called with 1 argument: an array of waypoints.

    callback(waypoints) {
        waypoints[0] == { x:value, y:value, z:value }
        ...
    }

## Basic agents operations
<a name="recast.addAgent" href="API#recast.addAgent">#</a> recast.<b>addAgent</b>(<i>options</i>)

Add an agent on the navmesh and returns its `agent_id`. Supported options are:

    position: { x:0, y:0, z:0 }, // initial position
    radius: 0.8,                 // agent radius
    height: 0.5,                 // agent height
    maxAcceleration: 1.0,        // maximum acceleration factor
    maxSpeed: 2.0,               // maximum speed
    updateFlags: 0,              // update flags
    separationWeight: 20.0       // separation factor

<a name="recast.updateCrowdAgentParameters" href="API#recast.updateCrowdAgentParameters">#</a> recast.<b>updateCrowdAgentParameters</b>(<i>int agent_id</i>, <i>options</i>)

Update an agent settings.

<a name="recast.removeCrowdAgent" href="API#recast.removeCrowdAgent">#</a> recast.<b>removeCrowdAgent</b>(<i>int agent_id</i>)

Remove an agent from the crowd


## Crowd
<a name="recast.initCrowd" href="API#recast.initCrowd">#</a> recast.<b>initCrowd</b>(<i>int max</i>, <i>float radius</i>)

Initialize the crowd system with a maximum of `max` agents and a radius reference of `radius`.

<a name="recast.crowdRequestMoveTarget" href="API#recast.crowdRequestMoveTarget">#</a> recast.<b>crowdRequestMoveTarget</b>(<i>int agent_id</i>, <i>dest_x</i>, <i>dest_y</i>, <i>dest_z</i>)

Set `agent_id`'s destination to `dest` point.

<a name="recast.crowdUpdate" href="API#recast.crowdUpdate">#</a> recast.<b>crowdUpdate</b>(<i>float time_delta</i>)

Tick the crowd system, and update all its agents positions. It internally emits an `update` event with the result of `crowdGetActiveAgents`.

<a name="recast.crowdGetActiveAgents" href="API#recast.crowdGetActiveAgents">#</a> recast.<b>crowdGetActiveAgents</b>(<i>callback</i>)

Retrieve all crowd agents. `callback` is called with 1 argument: an array containing all agents with their position.

    callback(agents) {
        agents[0].position      // current position
        agents[0].velocity      // current velocity
        agents[0].neighbors     // number of current neighbors
        agents[0].desiredSpeed  // desired speed
        ...
    }

<a name="recast.requestMoveVelocity" href="API#recast.requestMoveVelocity">#</a> recast.<b>requestMoveVelocity</b>(<i>int agent_id</i>, <i>float x</i>, <i>float y</i>, <i>float z</i>)

Set an agent's velocity. You can use this method to set an agent movements from gamepad values.


## Temporary obstacles
<a name="recast.addTempObstacle" href="API#recast.addTempObstacle">#</a> recast.<b>addTempObstacle</b>(<i>float x</i>, <i>float y</i>, <i>float z</i>, <i>float radius</i>)

Add a temporary obstacle at desired position with a specified radius.

<a name="recast.removeTempObstacle" href="API#recast.removeTempObstacle">#</a> recast.<b>removeTempObstacle</b>(<i>int obstacle_id</i>)

Remove `obstacle_id` temporary obstacle.

<a name="recast.getAllTempObstacles" href="API#recast.getAllTempObstacles">#</a> recast.<b>getAllTempObstacles</b>(<i>callback</i>)

Retrieve all temporary obstacles. `callback` is called with 1 argument: an array of all current temporary obstacles with their position and radius.

<a name="recast.clearAllTempObstacles" href="API#recast.clearAllTempObstacles">#</a> recast.<b>clearAllTempObstacles</b>()

Remove all temporary obstacles.


## Off-mesh connections
<a name="recast.addOffMeshConnection" href="API#recast.addOffMeshConnection">#</a> recast.<b>addOffMeshConnection</b>(<i>float from_x</i>, <i>float from_y</i>, <i>float from_z</i>, <i>float to_x</i>, <i>float to_y</i>, <i>float to_z</i>, <i>float radius</i>, <i>boolean both_directions</i>)

Add an off-mesh connection. If `both_directions` is true, connection will available in both directions.
