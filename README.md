**Introduction**

A very Simple resource that allows resources to run tasks asynchronously.

# fxserver-async
Async utilities for FXServer

[INSTALLATION]

Set it as a dependency in you __resource.lua

```
server_script '@async/async.lua'
```

[USAGE]

```
local tasks = {}

for i=1, 100, 1 do

	local task = function(cb)
		
		SetTimeout(1000, function()

			local result = math.random(1, 50000)

			cb(result)
			
		end)

	end

	table.insert(tasks, task)

end

Async.parallel(tasks, function(results)
	print(json.encode(results))
end)

Async.parallelLimit(tasks, 2, function(results)
	print(json.encode(results))
end)

Async.series(tasks, function(results)
	print(json.encode(results))
end)

```
