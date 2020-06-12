# Seltzer

Have you ever wished that you could perform medical functions by force feeding people 

Have you ever felt like the lack of sezlter in Barotrauma was a little weird? Well no more!


Medical Seltzer!

Seltzer with fun flavors! Seltzer with crazy functions! Blood Seltzer! Some sort of mineral water! We even change the  


Tonic Liquid -> Seltzer Liquid

Where's the CO2 come from? Don't ask such silly questions!

this video is so cool, I want to make it into a machine
https://www.youtube.com/watch?v=2cWa5ENWxAg


## Fire Extinguisher 

is crafted with sodium 


extinguisher uses Sodium bicarbonate as its agent which releases a cloud of carbon dioxide that smothers the fire


`Barotrauma\Content\Items\Tools\tools.xml`
```xml
<Item name="" identifier="extinguisher" category="Equipment" Tags="mediumitem,fireextinguisher,provocative" cargocontaineridentifier="metalcrate" description="" impactsoundtag="impact_metal_light">
    <Upgrade gameversion="0.9.600.0" Tags="mediumitem,fireextinguisher,provocative" />
    <PreferredContainer primary="extinguisherholder" spawnprobability="1.0"/>
    <PreferredContainer primary="engcab,reactorcab"/>
    <Price locationtype="City" buyprice="100" />
    <Price locationtype="Research" buyprice="100" />
    <Price locationtype="Military" buyprice="100" />
    <Price locationtype="Outpost" buyprice="150" />
    <Price locationtype="Mine" buyprice="100" />
    <Deconstruct time="10">
      <Item identifier="aluminium" />
    </Deconstruct>
    <Fabricate suitablefabricators="fabricator" requiredtime="10">
      <RequiredSkill identifier="mechanical" level="20" />
      <RequiredItem identifier="aluminium" />
      <RequiredItem identifier="sodium" />
    </Fabricate>
    <InventoryIcon texture="Content/Items/InventoryIconAtlas.png" sourcerect="0,0,64,64" origin="0.5,0.5" />
    <Sprite texture="Content/Items/InventoryIconAtlas.png" depth="0.55" sourcerect="0,0,64,64" origin="0.5,0.5" />
    <Body width="17" height="48" density="5" />
    <Holdable slots="RightHand+LeftHand" controlpose="false" aimpos="40,-20" handle1="-2,30" msg="ItemMsgPickUpSelect" />
    <RepairTool extinguishamount="60.0" range="500" barrelpos="21,25" repairthroughholes="true" hititems="false">
      <ParticleEmitter particle="extinguisher" velocitymin="500.0" velocitymax="650.0" particlespersecond="50" />
      <StatusEffect type="OnUse" targettype="This" Condition="-2.0" />
      <sound file="Content/Items/Tools/Extinguisher.ogg" type="OnUse" range="500.0" loop="true" />
    </RepairTool>
    <Propulsion force="-80" usablein="water" particles="bubbles" />
    <aitarget sightrange="1000" soundrange="1000" fadeouttime="1" />
  </Item>

```

`Barotrauma\Content\Items\Diving\divinggear.xml`
```xml
  <Item name="" identifier="oxygentank" category="Equipment,Misc" Tags="oxygentank,smallitem,oxygensource" cargocontaineridentifier="metalcrate" scale="0.3" impactsoundtag="impact_metal_light">
    <PreferredContainer primary="divingcab" minamount="1" maxamount="5" spawnprobability="1"/>
    <PreferredContainer primary="oxygengenerator"/>
    <PreferredContainer primary="divingsuit,divingmask,plasmacutter" spawnprobability="1.0"/>
    <PreferredContainer primary="supplycab" minamount="1" maxamount="1" spawnprobability="0.5"/>
    <Price locationtype="Research" buyprice="75" />
    <Price locationtype="City" buyprice="75" />
    <Price locationtype="Military" buyprice="75" />
    <Price locationtype="Outpost" buyprice="70" />
    <Deconstruct time="10">
      <Item identifier="aluminium" />
    </Deconstruct>
    <Fabricate suitablefabricators="fabricator" displayname="OxygenTankEmpty" outcondition="0.0">
      <RequiredItem identifier="aluminium" />
    </Fabricate>
    <InventoryIcon texture="Content/Items/InventoryIconAtlas.png" sourcerect="896,0,64,64" origin="0.5,0.5" />
    <Sprite texture="Content/Items/Tools/tools_new.png" sourcerect="356,223,39,110" depth="0.55" origin="0.5,0.5" />
    <Body width="38" height="109" density="5" />
    <Holdable slots="Any,RightHand,LeftHand" holdpos="30,-15" handle1="0,5" handle2="0,-5" msg="ItemMsgPickUpSelect">
      <StatusEffect type="OnFire" target="This" Condition="-100.0" disabledeltatime="true">
        <Conditional Condition="gt 25" />
        <sound file="Content/Items/Weapons/ExplosionSmall1.ogg" range="5000" />
        <sound file="Content/Items/Weapons/ExplosionDebris1.ogg" range="5000" />
        <Explosion range="250.0" structuredamage="10" force="3.0">
          <Affliction identifier="burn" strength="5" />
          <Affliction identifier="stun" strength="5" />
        </Explosion>
      </StatusEffect>
      <StatusEffect type="OnFire" target="This" Condition="-100.0" disabledeltatime="true" />
    </Holdable>
  </Item>
```

## Core Design 

Extends item to 4 uses and lowers level requirement

Can't be deconstructed (probably)

Affliction Fizzy 

Run faster and burp 
or
Does nothing

## Items

CO2 Canister 

#### Blood Seltzer

It appears this seltzer has regenerative capacities and dampens blood loss. Tastes like a fruity nail. 

Fabricator: Blood Pack + .10 CO2 Canister 

4 uses

Bloodloss -8%/s | 15s | med level 10  

Internal Damage -0.25%/s | 10s | med level 10 

#### Seltzer Liquid

Treats internal damage and slows metabolism. A distinct lack of quinine adds to the flavor.

Fabricator: Blood Pack + .10 CO2 Canister 

4 uses

Slow Metabolism 300% | 15s | med level 10  

Internal Damage -0.5%/s | 15s | med level 10  

#### Morphine Seltzer

Treats internal damage and slows metabolism. A distinct lack of quinine adds to the flavor.

Fabricator: Blood Pack + .10 CO2 Canister 

4 uses

Affliction Internal Damage.png Internal Damage (-5%/s | -2%/s)*
Affliction Burn.png Burn (-5%/s | -2%/s)*
Affliction Oxygen Low.png Oxygen Low (+2%/s | +3%/s)*
Affliction Opiate Addiction.png Opiate Addiction (+0.5%/s | +2.5%/s)*
Affliction Opiate Overdose.png Opiate Overdose (+1%/s | +2%/s)*
Affliction Opiate Withdrawal.png Opiate Withdrawal (-3%/s)*

#### Fentanyl Seltzer

#### Broad-spectrum Antibiotics Seltzer

#### Stable Seltzer

#### Oxygenated Seltzer

#### CalyxSeltzer

### Antidotes

#### DeliREEEEEE Seltzer (Cures Deliriumine Poisoning and treats Psychosis over time.)

#### MorbuPleaseLeave Seltzer (Cures Morbusine Poisoning.)

#### CyaBye Seltzer (Cures Cyanide Poisoning.)

#### SufforNoLonger Seltzer (Cures Sufforin Poisoning.)

#### RadAway Seltzer (Cures Radiation Sickness.)

### Poisons

#### Morbusine Seltzer (no thank you)

#### Sufforin Seltzer (the alteration is nice but the effect isn't)

#### Cyanide Seltzer (smells like bitter almonds)

#### Radioactive Seltzer (this is worse than activating a toilet bowl)

#### Carbonated Eggs (the eggs don't seem to mind the bubbles)

#### Tonic Water (we don't recommend drinking such a vile liquid)

### Other

#### Chloral Hydrate Selzter TODO Could get you drunk and stun or something


## Chemical Formulae

Hydrochloric acid = HCl

Ethanol = C2H5OH

Calcium carbonate = CaCO3

## Potential Recipes

Carbon + 33.4 % of Oxygen = 1C02 Canister

Calcium + Carbon + Oxygen = Calcium Carbonate

Calcium Carbonate + Sulphuric Acid = CO2 Canister


## Recipes Ideas

Sulphuric Acid maybe

Calcium carbonate with acid (hydrochloric acid) 
