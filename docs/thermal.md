---
hide:
  - pageTitle
---

<center>
<hr>
[![Header](https://github.com/UnhappyCodings/thoriumreactors/raw/1.20.1/thumbnail.png)](https://www.curseforge.com/minecraft/mc-mods/thorium-reactors)

### Introduction

Have your reactor set up? Next will be a Heat Exchanger to generate steam! <br>
Head up to [Recipes](#recipes) and start crafting on all needed blocks and items for the heat exchanger!

<br>
[Next > Turbine](turbine.md){ .md-button }
<br><br>
<hr>

### Multiblock Structure

#### Heat Exchanger

??? success "Materials"
    To build a Hext Exchanger like shown below in **Construction**, you need the following blocks:

    <div markdown="1" style="text-align:left;width: fit-content;">
    **25x** Thermal Conductor [Recipe](recipes.md/#conductor) <br>
    **15x** Thermal Sink [Recipe](recipes.md/#sink) <br>
    **4x** Thermal Valve [Recipe](recipes.md/#valve_1) <br>
    **1x** Thermal Controller [Recipe](recipes.md/#controller_1) <br>
    </div>

??? question "Construction"
    Click the buttons below to cycle between the construction steps!
    <img src="/img/thermal_build_1.png" id="thermal-build">

    <button class="md-button" onClick="previousImage();"> :fontawesome-solid-chevron-left: </button>
    <button class="md-button" onClick="nextImage();"> :fontawesome-solid-chevron-right: </button>

    <div id="thermal_desc_1" markdown="1"> 

    <br> <em>**Description**</em> <br><br>
    Basic foundation is a 3x3 floor with two additional opposing blocks made out of [Thermal Conductor](recipes.md/#conductor). <br>
    The four corners need to be filled with [Thermal Valve](recipes.md/#valve_1)!
    
    <br>
    </div>
    
    <div id="thermal_desc_2" hidden> 

    <br><em>**Description**</em> <br><br>
    Next you need one [Thermal Controller](recipes.md/#controller_1) in the mid of one if the two side with 5 block length! <br>
    Fill the rest of the layer with [Thermal Conductor](recipes.md/#conductor)! <br>

    <br>
    </div>
    
    <div id="thermal_desc_3" hidden> 

    <br><em>**Description**</em> <br><br>
    Lastly fill the last layer with [Thermal Sinks](recipes.md/#sink)! <br>
    
    <p style="color:#d60000"> Remember that the multiblock does not give you instant feedback when its build correctly!</p>
    
    <br>
    </div>
<hr>

### Usage

#### Enabling the Heat Exchanger

<div markdown="1" style="text-align:left;">
After you have built up your heat exchanger, click on its [Thermal Controller](recipes.md/#controller_1) to activate the multiblock structure!
The activation is indicated by green particles around the multiblock and the controller should have turned on!
Otherwise, check your structure again to see if it fits the conditions in [Multiblock Structure](#multiblock-structure).
</div>

<br>

#### Usage

<div markdown="1" style="text-align:left;">
Take a [Configurator](recipes.md/#configurator) and click on each [Thermal Valve](recipes.md/#controller_2) to configure the in- or outputs! 
Into the Coolant Input you'll insert water, on the Coolant Output the produced steam will come out!
Same for the Heat Input, where you'll insert the Heated Molten Salt, on the Heat Output will the Depleted Molten Salt extracted!

That extracted Depleted Molten Salt is need to be enriched again. For that take a [Fluid Enricher](recipes.md/#fluid-enricher) and insert the fluid and thorium!
</div>
<br>

<hr>

<script>

  function nextImage() {
    let element = document.getElementById("thermal-build");
    let src = element.src;
    let nextInt = parseInt(src.split("build_")[1].split(".")[0]) + 1;
    if (nextInt <= 5) {
      document.getElementById("thermal_desc_" + nextInt).hidden = false;
      document.getElementById("thermal_desc_" + (nextInt - 1)).hidden = true;
      element.src = "/img/thermal_build_" + nextInt + ".png";
    }
  }

  function previousImage() {
    let element = document.getElementById("thermal-build");
    let src = element.src;
    let nextInt = parseInt(src.split("build_")[1].split(".")[0]) - 1;
    if (nextInt >= 1) {
      document.getElementById("thermal_desc_" + nextInt).hidden = false;
      document.getElementById("thermal_desc_" + (nextInt + 1)).hidden = true;
      element.src = "/img/thermal_build_" + nextInt + ".png";
    }
  }

</script>