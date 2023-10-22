---
hide:
  - pageTitle
---

<center>
<hr>
[![Header](https://github.com/UnhappyCodings/thoriumreactors/raw/master/thumbnail.png)](https://www.curseforge.com/minecraft/mc-mods/thorium-reactors)

### Introduction

Finally have all fueling ingredients to start your reactor? Great! <br>
Head up to [Recipes](#recipes) and start crafting on all needed blocks for your own reactor!

<br>
[Next > Turbine](turbine.md){ .md-button }
<br><br>
<hr>

### Multiblock Structure

#### Reactor

??? success "Materials"
    To build a Thorium Reactor like shown below in **Construction**, you need the following blocks:

    <div markdown="1" style="text-align:left;width: fit-content;">
    **61x** Reactor Casing [Recipe](recipes.md/#casing) <br>
    **31x** Reactor Glass [Recipe](recipes.md/#glass) <br>
    **4x** Reactor Valve [Recipe](recipes.md/#valve) <br>
    **2x** Graphite Moderator [Recipe](recipes.md/#graphite-moderator) <br>
    **1x** Reactor Rod Controller [Recipe](recipes.md/#rod-controller) <br>
    **1x** Reactor Controller [Recipe](recipes.md/#controller) <br>
    **1x** Reactor Core [Recipe](recipes.md/#core) <br>
    </div>

??? question "Construction"
    Click the buttons below to cycle between the construction steps!
    <img src="/img/reactor_build_1.png" id="reactor-build">

    <button class="md-button" onClick="previousImage();"> :fontawesome-solid-chevron-left: </button>
    <button class="md-button" onClick="nextImage();"> :fontawesome-solid-chevron-right: </button>

    <div id="reactor_desc_1" markdown="1"> 

    <br> <em>**Description**</em> <br><br>
    Basic foundation is a 5x5 floor made out of [Reactor Casing](recipes.md/#casing).

    <br>
    </div>
    
    <div id="reactor_desc_2" hidden> 

    <br><em>**Description**</em> <br><br>
    Next you need four framing [Reactor Casing](recipes.md/#casing) one in each corner! <br>
    After that place four [Reactor Valve](recipes.md/#valve) two of them each, need to be on the opposing site of to the other two. <br>
    You'll need one [Reactor Controller](recipes.md/#controller) in one of the two sides where no valves are. <br>
    Fill every other framing block up with [Reactor Glass](recipes.md/#glass)! <br>
    Last but not least place a [Reactor Core](recipes.md/#core) in the 5x5 middle!

    <br>
    </div>
    
    <div id="reactor_desc_3" hidden> 

    <br><em>**Description**</em> <br><br>
    Next you need four framing [Reactor Casing](recipes.md/#casing) one in each corner! <br>
    Place on [Graphite Moderator](recipes.md/#moderator) in the 5x5 middle! <br>
    Fill every other framing block up with [Reactor Glass](recipes.md/#glass)! <br>
    
    <p style="color:#d60000"> <b> Important Information! </b> <br>
    You can build this layer one to three times, this only changes the reactors height. <br>
    Production rates are not affected by that! </p>
    
    <br>
    </div>
    
    <div id="reactor_desc_4" hidden> 

    <br><em>**Description**</em> <br><br>
    Next you need four framing [Reactor Casing](recipes.md/#casing) one in each corner! <br>
    Place on [Graphite Moderator](recipes.md/#moderator) in the 5x5 middle! <br>
    Fill every other framing block up with [Reactor Glass](recipes.md/#glass)! <br>
    
    <p style="color:#d60000"> <b> Important Information! </b> <br>
    You can build this layer one to three times, this only changes the reactors height. <br>
    Production rates are not affected by that! </p>
    
    <br>
    </div>
    
    <div id="reactor_desc_5" hidden>

    <br><em>**Description**</em> <br><br>
    Lastly place a [Rod Controller](recipes.md/#rod-controller), again, in the middle of the 5x5 structure. <br>
    Fill all other blocks with [Reactor Casing](recipes.md/#casing)!

    <p style="color:#d60000"> Remember that the multiblock does not give you instant feedback when its build correctly!</p>
    
    <br>
    </div>

??? tip "Allowed sizes"
    Click the buttons below to cycle between the allowed sizes!
    <img src="/img/reactor_height_4.png" id="reactor-height">

    <button class="md-button" onClick="previousHeightImage();"> :fontawesome-solid-chevron-left: </button>
    <button class="md-button" onClick="nextHeightImage();"> :fontawesome-solid-chevron-right: </button>

<hr>

### Usage

#### Enabling the reactor

<div markdown="1" style="text-align:left;">
After you have **finally** built up your reactor, click on its [Reactor Controller](recipes.md/#controller) to activate the multiblock structure!
The activation is indicated by green particles around the multiblock and the controller should have turned on!
Otherwise, check your structure again to see if it fits the conditions in [Multiblock Structure](#multiblock-structure).
</div>
<br>

#### Controlling

<div markdown="1" style="text-align:left;">
Finally you can open your **reactor interface** by clicking on the **controller** again! <br>
Here you can see all future statistics for your reactor and turbine as temp, fuel, status, time, speed, generation and much more! <br>
Dont forget to open the left and right side to get all types of information!
</div>
<br>

#### Fuel it up

<div markdown="1" style="text-align:left;">
To **fuel up your reactor** in any way (item, fluid) you will need to configure the **reactor valves**. <br>
For that, equip your [Configurator](recipes.md/#configurator) and right-click on the **valves** to set them to your desired mode. <br>
Use some kind of **pipes/cables** to firstly fuel your **molten salt** though the **Fluid Input** valve mode in the reactor! <br>
Any size of reactor does atleast need **8.000mB** of **molten salt** to not end up in a scram shutdown!

After that, fuel it up with **enriched uranium** through the **Item Input** valve mode. <br>
For that you need to open the **reactor interface** and change the **FUEL LOAD** value and confirm it with **SET**. <br>
You will see that the **in the valves stored** enriched uranium will be **consumed** by the reactor. <br>
The rod grid in the **interface** should come up in **green** after some time!

Its ***very important*** that you fill up the reactor with atleast 8.000mB **molten salt** before you fuel it with **enriched uranium**! <br>
Otherwise the **massive chain reaction** will emit **huge amounts of radiation**!
</div>
<br>

#### First startup

<div markdown="1" style="text-align:left;">
After you have **filled up the reactor** with **molten salt** and fueled it with **enriched uranium**, try a startup!
Increase your **ROD INSERT** value depending on your **fuel level**. For the first run set it to some **save/secure** value, e.g. 70%.
This will make sure, that the **reactor** will run at **30%** of its current maximum capability!

Its important that you pay attention to the **Reactor Load** value after you started the reactor, <br>
it should stay at or **under 100%**. When reaching states **over 105% it gets damaged**! <br>
Damaging a reactor is obviously a bad idea, don't do it! Don't try it! **Never!** <br>
Its decreasing the **reachable temperature**, **fluid conversion rate**, and even lets **radiation escape**. <br>
A damaged reactor **cannot** be repaired! Luckily, a thorium reactor **cannot** explode!

Now simply click on **START** to activate the reactors physical chain reaction. <br>
The reactor will now heat up to its maximum temperature defined by the current configuration! <br>
Now you can modify the **Reactor Load** value to savely bring it to 100%. Remember that more uranium means more heat! <br>
When it's heated up, switch from **START** to **RUN**! This change will let the reactor **heat up** the before fueled **molten salt** into its **heated form**. <br>
The rate of that transformation is set at **1mB** per 50°C each tick (1 sec = 20 ticks) beginning at **101°C with 2mB**. So e.g. the reactor will generate **20mB/t at 1000°C**!

Secondary, a **depleted uranium** pellet is being spit out **each 12 hours** of active reactor **running** time!
Make sure, that such **can be extracted** though valves in **Item Output** mode. <br>
Otherwise the **molten salt conversion** and temperature are decreasing drastically! <br>
Pump out the heated molten salt through a valve in **Fluid Output** mode.

Always keep an eye on your reactor load! **Alarm sounds** appear when it gets too high or its scrammed!

**Changes to this text may apply! As of 03.10.2023.**
</div>
<br>

<hr>

<script>

  function nextHeightImage() {
    let element = document.getElementById("reactor-height");
    let src = element.src;
    let nextInt = parseInt(src.split("height_")[1].split(".")[0]) + 1;
    if (nextInt <= 6) {
      element.src = "/img/reactor_height_" + nextInt + ".png";
    }
  }

  function previousHeightImage() {
    let element = document.getElementById("reactor-height");
    let src = element.src;
    let nextInt = parseInt(src.split("height_")[1].split(".")[0]) - 1;
    if (nextInt >= 4) {
      element.src = "/img/reactor_height_" + nextInt + ".png";
    }
  }

  function nextImage() {
    let element = document.getElementById("reactor-build");
    let src = element.src;
    let nextInt = parseInt(src.split("build_")[1].split(".")[0]) + 1;
    if (nextInt <= 5) {
      document.getElementById("reactor_desc_" + nextInt).hidden = false;
      document.getElementById("reactor_desc_" + (nextInt - 1)).hidden = true;
      element.src = "/img/reactor_build_" + nextInt + ".png";
    }
  }

  function previousImage() {
    let element = document.getElementById("reactor-build");
    let src = element.src;
    let nextInt = parseInt(src.split("build_")[1].split(".")[0]) - 1;
    if (nextInt >= 1) {
      document.getElementById("reactor_desc_" + nextInt).hidden = false;
      document.getElementById("reactor_desc_" + (nextInt + 1)).hidden = true;
      element.src = "/img/reactor_build_" + nextInt + ".png";
    }
  }

</script>