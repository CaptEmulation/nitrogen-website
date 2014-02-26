class Agent
-----------
**Methods**

Agent.create(session, callback, callback.err, callback.principal)
-----------------------------------------------------------------
Create an agent in the Nitrogen service.  If it marked enabled, this will also start the agent on the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback for the create.

**callback.err**:  *Object*,  If the create failed, this will contain the error.

**callback.principal**:  *Object*,  The created agent returned by the service.

Agent.find(session, query, options, options.limit, options.sort, options.dir, options.skip, callback, callback.err, callback.agents)
----------------------------------------------------------------------------------------------------
Find agents filtered by the passed query and limited to and sorted by the passed options.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query using MongoDB query format.

**options**:  *Object*,  Options for the query.

**options.limit**:  *Number*,  The maximum number to be returned.

**options.sort**:  *String*,  The field that the results should be sorted on.

**options.dir**:  *Number*,  The direction that the results should be sorted.

**options.skip**:  *Object*,  The number of results that should be skipped before pulling results.

**callback**:  *Object*,  Callback at completion of execution.

**callback.err**:  *Object*,  If the find failed, find will callback with the error.

**callback.agents**:  *Array*,  The set found with this query.

Agent.save(session, callback, callback.err, callback.agent)
-----------------------------------------------------------
Save this agent to the service.  If the agent is now not enabled and active, the agent will be stopped.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback for the save.

**callback.err**:  *Object*,  If the save failed, this will contain the error.

**callback.agent**:  *Object*,  The saved agent returned by the service.

