---
hide:
  - pageTitle
---

<center>
<hr>
[![Header](https://github.com/UnhappyCodings/thoriumreactors/raw/master/thumbnail.png)](https://www.curseforge.com/minecraft/mc-mods/thorium-reactors)

### Introduction

You can also use [Computer Craft: Tweaked](https://www.curseforge.com/minecraft/mc-mods/cc-tweaked) to control your reactor and turbines!
For that, some knowledge in LUA or even in CC:Tweaked would be great! 

You can use any [Reactor Casing](recipes.md/#casing) as peripheral, as long as the reactor has been assembled once before!

<br><br>
<hr>
</center>

## Peripheral
Peripheral Name
```
thorium_reactor
```

Example
```lua
local reactor = peripheral.find("thorium_reactor")
```
<hr>

## Example Script

![Computer Example Script](/img/computer-example-script.png)

??? success "Show Script"
    ```lua linenums="1" title="startup.lua"
    reactor = peripheral.find("thorium_reactor")
    monitor = peripheral.find("monitor")
    
    monitor.clear()
    
    monitor.setCursorPos(15,1)
    monitor.write("Turbine")
    monitor.setCursorPos(1,2)
    monitor.write("Turbines: " .. reactor.getTurbineCount())
    
    offset = 3
    for i=reactor.getTurbineCount() - 1,0,-1 do
        monitor.setCursorPos(1,offset)
        monitor.write("Turbine #" .. i)
        monitor.setCursorPos(20,offset)
        monitor.write("x:" .. reactor.getTurbinePosition(i).x .. " y:" .. reactor.getTurbinePosition(i).y .. " z:" .. reactor.getTurbinePosition(i).z)
        monitor.setCursorPos(20,offset + 1)
        monitor.write(tostring(reactor.isTurbineActive(i) and "Active" or "Inactive"))
        monitor.setCursorPos(30,offset + 1)
        monitor.write(tostring(reactor.isTurbineAssembled(i) and "Assembled" or "Incomplete"))
        monitor.setCursorPos(20,offset + 2)
        monitor.write(string.format("%.1f", reactor.getTurbineGeneration(i)) .. "FE/t")
        monitor.setCursorPos(20,offset + 3)
        monitor.write(string.format("%.1f", reactor.getTurbineSpeed(i)) .. "RPM")
        monitor.setCursorPos(30,offset + 3)
        monitor.write(string.format("%.1f", reactor.getTurbineHeight(i)) .. "B")
        monitor.setCursorPos(20,offset + 4)
        monitor.write(tostring(reactor.getTurbineCurrentFlow(i)) .. " / " .. tostring(reactor.getTurbineTargetFlow(i)) .. "mB/t")
        offset = offset + 5
    end
    
    offset = offset + 1
    monitor.setCursorPos(15,offset)
    monitor.write("Reactor")
    monitor.setCursorPos(1,offset + 1)
    monitor.write(reactor.isAssembled() and "Assembled" or "Incomplete")
    monitor.setCursorPos(30,offset + 1)
    monitor.write(string.upper(reactor.getReactorState()))
    monitor.setCursorPos(1,offset + 2)
    monitor.write("Temperature: " .. string.format("%.1f", reactor.getReactorCurrentTemperature()) .. " / " .. string.format("%.1f", reactor.getReactorTargetTemperature()) .. "°C")
    monitor.setCursorPos(1,offset + 3) 
    monitor.write("Molten Salt: " .. tostring(reactor.getReactorFluidAmountIn()) .. " / " .. tostring(reactor.getReactorFluidCapacityIn()) .. "mB")
    monitor.setCursorPos(1,offset + 4) 
    monitor.write("Heated Molten Salt: " .. tostring(reactor.getReactorFluidAmountOut()) .. " / " .. tostring(reactor.getReactorFluidCapacityOut()) .. "mB")
    ```
<hr>

## Functions

### ***isAssembled()***

<h5> Description </h5>

Returns true or false whether the reactor is assembled or not!

<h5> Method </h5>

```lua 
isAssembled() -> boolean
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Assembled? " .. tostring(reactor.isAssembled()))
```

<hr>

### ***getReactorState()***

<h5> Description </h5>

Returns the current operating mode of the reactor as a string.

<h5> Method </h5>

```lua 
getReactorState() -> string

return: "starting", "running", "stop"
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Currently in " .. tostring(reactor.getReactorState() .. " mode!"))
```

<hr>

### ***setReactorState()***

<h5> Description </h5>

Set the reactor operating state!
When an invalid mode is passed, the reactor will use "stop" as default.

<h5> Method </h5>

```lua 
setReactorState(string mode)

mode: "starting", "running", "stop"
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setReactorState("starting")
```

<hr>

### ***getReactorFluidAmountOut()***

<h5> Description </h5>

Returns the amount of **heated** molten salt in the reactor tank!

<h5> Method </h5>

```lua 
getReactorFluidAmountOut() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Heated Molten Salt: " .. tostring(reactor.getReactorFluidAmountOut()) .. " mB")
```

<hr>

### ***getReactorFluidCapacityOut()***

<h5> Description </h5>

Returns the capacity of the reactor output tank! (Heated Molten Salt)

<h5> Method </h5>

```lua 
getReactorFluidCapacityOut() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Capacity Out: " .. tostring(reactor.getReactorFluidCapacityOut()) .. " mB")
```

<hr>

### ***getReactorFluidAmountIn()***

<h5> Description </h5>

Returns the amount of molten salt in the reactor tank!

<h5> Method </h5>

```lua 
getReactorFluidAmountIn() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Molten Salt: " .. tostring(reactor.getReactorFluidAmountIn()) .. " mB")
```

<hr>

### ***getReactorFluidCapacityIn()***

<h5> Description </h5>

Returns the capacity of the reactor input tank! (Molten Salt)

<h5> Method </h5>

```lua 
getReactorFluidCapacityIn() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Capacity In: " .. tostring(reactor.getReactorFluidCapacityIn()) .. " mB")
```

<hr>

### ***getReactorCapacity()***

<h5> Description </h5>

Returns the total capacity of the reactor!

<h5> Method </h5>

```lua 
getReactorCapacity() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Capacity: " .. tostring(reactor.getReactorCapacity()) .. " mB")
```

<hr>

### ***getReactorCurrentLoadSet()***

<h5> Description </h5>

Returns the value of current fueled uranium in percent!

<h5> Method </h5>

```lua 
getReactorCurrentLoadSet() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Uranium Fuel: " .. tostring(reactor.getReactorCurrentLoadSet()) .. "%")
```

<hr>

### ***getReactorTargetLoadSet()***

<h5> Description </h5>

Returns the set/wanted uranium fuel fill level in percent!

<h5> Method </h5>

```lua 
getReactorTargetLoadSet() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Uranium Fuel: " .. tostring(reactor.getReactorTargetLoadSet()) .. "%")
```

<hr>

### ***setReactorTargetLoadSet()***

<h5> Description </h5>

Set the wanted uranium fuel fill level in percent!

<h5> Method </h5>

```lua 
setReactorTargetLoadSet(Integer rate)

rate: 0 - 100
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setReactorTargetLoadSet(100)
```

<hr>

### ***getReactorStatusPercent()***

<h5> Description </h5>

Returns the current health rate of the reactor in percent!

<h5> Method </h5>

```lua 
getReactorStatusPercent() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Health: " .. tostring(reactor.getReactorStatusPercent()) .. "%")
```

<hr>

### ***getReactorContainmentPercent()***

<h5> Description </h5>

Returns the current containment rate of the reactor in percent!

<h5> Method </h5>

```lua 
getReactorContainmentPercent() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Health: " .. tostring(reactor.getReactorContainmentPercent()) .. "%")
```

<hr>

### ***getReactorRadiation()***

<h5> Description </h5>

Returns the current escaping radiation of the reactor in µSv!

<h5> Method </h5>

```lua 
getReactorRadiation() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Radiation: " .. tostring(reactor.getReactorRadiation()) .. "uSv")
```

<hr>

### ***isReactorScrammed()***

<h5> Description </h5>

Returns whether the reactor is scrammed or not!

<h5> Method </h5>

```lua 
isReactorScrammed() -> boolean
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Scrammed? " .. tostring(reactor.isReactorScrammed()))
```

<hr>

### ***setReactorScrammed()***

<h5> Description </h5>

Set the reactor operating state!
When an invalid mode is passed, the reactor will use "stop" as default.

<h5> Method </h5>

```lua 
setReactorScrammed(boolean state)

state: true, false
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setReactorScrammed(true)
```

<hr>

### ***getReactorRunningSince()***

<h5> Description </h5>

Returns the time the reactor has run until last startup!
Format: 5 seconds = 5 seconds * 20 ticks = 100

<h5> Method </h5>

```lua 
getReactorRunningSince() -> Long
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Time lasted: " .. tostring(reactor.getReactorRunningSince() / 20))
```

<hr>

### ***getReactorCurrentTemperature()***

<h5> Description </h5>

Returns the reactors current temperature in degree Celsius!

<h5> Method </h5>

```lua 
getReactorCurrentTemperature() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Current Temp: " .. tostring(reactor.getReactorCurrentTemperature()) .. "°C")
```

<hr>

### ***getReactorTargetTemperature()***

<h5> Description </h5>

Returns the reactors target temperature in degree Celsius!

<h5> Method </h5>

```lua 
getReactorTargetTemperature() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Target Temp: " .. tostring(reactor.getReactorTargetTemperature()) .. "°C")
```

<hr>

### ***getReactorNotification()***

<h5> Description </h5>

Returns the current notification of the reactor!
For example when the reactor gets scrammed!

<h5> Method </h5>

```lua 
getReactorNotification() -> String
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Warning: " .. reactor.getReactorNotification())
```

<hr>

### ***getReactorLoad()***

<h5> Description </h5>

Returns the load of the reactor!

<h5> Method </h5>

```lua 
getReactorLoad() -> Float
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Warning: " .. toString(reactor.getReactorLoad()))
```

<hr>

### ***getFuelRodStatus()***

<h5> Description </h5>

Returns the fuel level of the given fuel rod in percent!

<h5> Method </h5>

```lua 
getFuelRodStatus(Integer index) -> Float

index: 0 - 63
```

<hr>

### ***getFuelRodStatusMap()***

<h5> Description </h5>

Returns the fuel level of the given fuel rod in percent in a lua table!

<h5> Method </h5>

```lua 
getFuelRodStatusMap() -> Table: Int, Int
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

for k, v in pairs(reactor.getFuelRodStatusMap()) do
    print("Fuel #: " .. k .. " has " .. v .. "% fuel")
end
```

<h5> Added In </h5>

ThoriumReactors version 0.2b


<hr>

### ***getDepletedFuelRodStatus()***

<h5> Description </h5>

Returns the depleted fuel level of the given fuel rod in percent!

<h5> Method </h5>

```lua 
getDepletedFuelRodStatus(Integer index) -> Float

index: 0 - 63
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Depletion #55: " .. toString(reactor.getDepletedFuelRodStatus(55)) .. "%")
```

<hr>

### ***getDepletedFuelRodStatusMap()***

<h5> Description </h5>

Returns the depleted fuel level of the given fuel rod in percent in a lua table!

<h5> Method </h5>

```lua 
getDepletedFuelRodStatusMap() -> Table: Int, Int
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

for k, v in pairs(reactor.getDepletedFuelRodStatusMap()) do
    print("Fuel #: " .. k .. " has " .. v .. "% depleted fuel")
end
```

<h5> Added In </h5>

ThoriumReactors version 0.2b


<hr>

### ***getCurrentControlRodStatus()***

<h5> Description </h5>

Returns the current control rod insert value in percent!

<h5> Method </h5>

```lua 
getCurrentControlRodStatus(Integer index) -> Float

index: 0 - 80
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Control #55: " .. toString(reactor.getCurrentControlRodStatus(70)) .. "%")
```

<hr>

### ***getCurrentControlRodStatusMap()***

<h5> Description </h5>

Returns the depleted fuel level of the given fuel rod in percent in a lua table!

<h5> Method </h5>

```lua 
getCurrentControlRodStatusMap() -> Table: Int, Int
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

for k, v in pairs(reactor.getCurrentControlRodStatusMap()) do
    print("Rod #: " .. k .. " is " .. v .. "% inserted")
end
```

<h5> Added In </h5>

ThoriumReactors version 0.2b


<hr>

### ***getTargetControlRodStatus()***

<h5> Description </h5>

Returns the target control rod insert value in percent!

<h5> Method </h5>

```lua 
getTargetControlRodStatus(Integer index) -> Float

index: 0 - 80
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Control #70: " .. toString(reactor.getTargetControlRodStatus(70)) .. "%")
```

<hr>

### ***getTargetControlRodStatusMap()***

<h5> Description </h5>

Returns the depleted fuel level of the given fuel rod in percent in a lua table! <br>

<h5> Method </h5>

```lua 
getTargetControlRodStatusMap() -> Table: Int, Int
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

for k, v in pairs(reactor.getTargetControlRodStatusMap()) do
    print("Rod #: " .. k .. " will be " .. v .. "% inserted")
end
```

<h5> Added In </h5>

ThoriumReactors version 0.2b

<hr>

### ***setTargetControlRodStatus()***

<h5> Description </h5>

Sets the target control rod insert value!

<h5> Method </h5>

```lua 
setTargetControlRodStatus(Integer index, Integer value)

index: 0 - 80
value: 0 - 100
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

-- Sets target control rod insert to 59% on rod #10
reactor.setTargetControlRodStatus(10, 59)
```

<hr>

### ***isTurbineActive()***

<h5> Description </h5>

Returns true or false whether the turbine with the id is active.

<h5> Method </h5>

```lua 
isTurbineActive(Integer index) -> boolean

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Turbine on? " .. tostring(reactor.isTurbineActive(0)))
```

<hr>

### ***setTurbineActive()***

<h5> Description </h5>

Sets the activation state of a turbine.

<h5> Method </h5>

```lua 
setTurbineActive(Integer index, Boolean state)

index: 0 - ?
state: true - false
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setTurbineActive(0,true)
```

<hr>

### ***isTurbineCoilsEngaged()***

<h5> Description </h5>

Returns true or false whether the turbine coils are engaged or not.

<h5> Method </h5>

```lua 
isTurbineCoilsEngaged(Integer index) -> boolean

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Coils engaged? " .. tostring(reactor.isTurbineCoilsEngaged(0)))
```

<hr>

### ***setTurbineCoilsEngaged()***

<h5> Description </h5>

Sets the coil engage state of a turbine.

<h5> Method </h5>

```lua 
setTurbineCoilsEngaged(Integer index, Boolean state)

index: 0 - ?
state: true - false
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setTurbineCoilsEngaged(0,true)
```

<hr>

### ***copyConfigurationToAllTurbines()***

<h5> Description </h5>

Copy the settings from the given turbine to all others.

<h5> Method </h5>

```lua 
copyConfigurationToAllTurbines(Integer index)

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

-- copies all settings from turbine 0 to all other saved!
reactor.copyConfigurationToAllTurbines(0)
```

<hr>

### ***isTurbineAssembled()***

<h5> Description </h5>

Returns true or false whether the turbine is assembled or not.

<h5> Method </h5>

```lua 
isTurbineAssembled(Integer index) -> boolean

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Assembled? " .. tostring(reactor.isTurbineAssembled(0)))
```

<hr>

### ***getTurbineHeight()***

<h5> Description </h5>

Returns the total height of the turbine.

<h5> Method </h5>

```lua 
getTurbineHeight(Integer index) -> Integer

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Height: " .. tostring(reactor.getTurbineHeight(0)))
```

<hr>

### ***getTurbineCurrentFlow()***

<h5> Description </h5>

Returns the actual flow rate of the turbine.

<h5> Method </h5>

```lua 
getTurbineCurrentFlow(Integer index) -> Integer

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Flow rate: " .. tostring(reactor.getTurbineCurrentFlow(0)) "mB/t")
```

<hr>

### ***getTurbineTargetFlow()***

<h5> Description </h5>

Returns the target flow rate of the turbine.

<h5> Method </h5>

```lua 
getTurbineTargetFlow(Integer index) -> Integer

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Flow rate: " .. tostring(reactor.getTurbineTargetFlow(0)) .. "mB/t")
```

<hr>

### ***setTurbineTargetFlow()***

<h5> Description </h5>

Sets the target flow rate of the turbine.

<h5> Method </h5>

```lua 
setTurbineTargetFlow(Integer index, Integer flowrate)

index: 0 - ?
index: 0 - 2500
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

reactor.setTurbineTargetFlow(0,2000)
```

<hr>

### ***getTurbineGeneration()***

<h5> Description </h5>

Returns the target flow rate of the turbine.

<h5> Method </h5>

```lua 
getTurbineGeneration(Integer index) -> Float

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Gen: " .. tostring(reactor.getTurbineGeneration(0)) .. " FE/t")
```

<hr>

### ***getTurbineSpeed()***

<h5> Description </h5>

Returns the current turbine speed of the turbine.

<h5> Method </h5>

```lua 
getTurbineSpeed(Integer index) -> Float

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Speed: " .. tostring(reactor.getTurbineSpeed(0)) .. " RPM")
```

<hr>

### ***getTurbineEnergyModifier()***

<h5> Description </h5>

Returns the current turbine speed of the turbine.

<h5> Method </h5>

```lua 
getTurbineEnergyModifier(Integer index) -> Float

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Energy Modifier: " .. tostring(reactor.getTurbineEnergyModifier(0)) .. "x")
```

<hr>

### ***getTurbinePosition()***

<h5> Description </h5>

Returns the turbines position in a table.

<h5> Method </h5>

```lua 
getTurbinePosition(Integer index) -> Table

Table:
{
    "x": -127,
    "y": 80,
    "z": 322
}

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Position: x:" .. reactor.getTurbinePosition(0).x .. " y:" .. reactor.getTurbinePosition(0).y .. " z:" .. reactor.getTurbinePosition(0).z)
```

<hr>

### ***getTurbinePositionString()***

<h5> Description </h5>

Returns the turbines position in a string.

<h5> Method </h5>

```lua 
getTurbinePosition(Integer index) -> String

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Position: " + getTurbinePositionString())
```

<hr>

### ***getTurbinePositions()***

<h5> Description </h5>

Returns all turbines positions in a table.

<h5> Method </h5>

```lua 
getTurbinePositions(Integer index) -> Table

Table:
{
    {
        "x": -127,
        "y": 80,
        "z": 322
        "turbineId": 0
    },
    {
        "x": -127,
        "y": 80,
        "z": 322
        "turbineId": 1
    }
}

index: 0 - ?
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

local positions = reactor.getTurbinePositions(0)

for k, v in pairs(positions) do
    print(v.x .. " " .. v.y .. " " .. v.z .. " " .. v.turbineId)
end
```

<hr>

### ***getTurbineCount()***

<h5> Description </h5>

Returns the amount of all turbines.

<h5> Method </h5>

```lua 
getTurbineCount() -> Integer
```

<h5> Example </h5>

```lua linenums="1" title="example.lua"
local reactor = peripheral.find("thorium_reactor")

print("Turbines: " + reactor.getTurbineCount())
```

<hr>