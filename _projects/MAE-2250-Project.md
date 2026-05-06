---
layout: project
title: 2250 Client Document
description: MAE 2250
technologies: []
image: 
---
# Table of Contents <br />
[Exploratory Prototype](#exploratory-prototype) <br />
[First Prototype](#first-prototype) <br />
[Final Prototype](#final-prototype) <br />

# Exploratory Prototype
Title and Team Name: Proposed Methods of Spotted Lantern Fly Removal by The Grape. <br />
Client(s): Cornell CALS Extension / E&J Gallo Winery / National Grape <br />
Problem Statement: The removal of adult SLF from grape plants could damage or otherwise contaminate the plants or harvested grapes. Methods requiring the discernment between SLF and grape plants increase the complexity of removal or deterrence methods. Additionally, methods with physical contact between a device and plant may damage the grapes or plants, kill the SLF while still on the plants, or expose the grapes to potentially toxic quassinoids from the SLF remains. Also, chemical pesticides are ineffective against SLF, and increasing pesticide strength poses potential risks to the grape plants.  <br /> <br />
Impact: Removal or deterrence of SLF without harming vines would result in higher grape yields, minimize dependence on current ineffective chemical control methods, and reduce the time spent monitoring, spraying, or manually removing SLF, resulting in lower labor costs. 
Proposed Directions:  <br /> <br />
A ‘vacuum’ attached to the harvester to remove SLFs without damaging or removing grape plants. <br />
- Minimum viable product: A small-scale suction device that attaches to harvester and removes SLF into capture chamber without damaging grape plant (removing leaves or grapes, ripping stems) <br />
- Long term: A large-scale device with adjustable suctioning power that efficiently removes SLFs into a capture chamber without damaging grape plants. It attaches to harvester in front of the shaker, allowing access to vines for removal of lantern flies before the grapes are shaken off and added to the harvest. <br /> <br />
A decoy device that attracts SLF away from grape plants and then exterminates them. <br />
- Minimum viable product: A small-scale device that draws SLF away from grape plants either through one or more lures (frequency, shape, scent mimicking the Tree of Heaven, light). Uses a capturing mechanism that allows for mass collection of attracted SLF and simple removal/elimination. <br />
- Long term: Multiple larger devices that can be stationed throughout different-sized grape farms. <br /> <br />
Key risks/unknowns:  <br />
Suctioning device:  <br />
SLF at different life stages have different grip strengths, and can be removed with wind speeds varying from 64 km/h to 83.8 km/h (Elsensohn et al.)  <br />
Device may unintentionally vacuum smaller grapes or other parts of the grape plants
SLF may be stuck where the device cannot reach/maintain strong airflow <br />
Mechanical complexity may interfere with harvester or require high maintenance <br /> <br />
Decoy device: <br />
Effectiveness of various SLF attraction methods requires more research  <br />
Attraction methods may attract other harmful insects or creatures  <br /> <br />
Questions for Client:  <br />
Can a harvester be easily modified to feature the suctioning device? Is there a location on the harvester where it can be strategically placed before the vines reach the shaker? <br />
If there is no effective location for this device to be mounted, it will not be viable. <br />
How important is it to farmers that the SLF are removed? Is it worth risking damage to 10%, 20%, or more of their plants to ensure that their harvests are SLF free? <br />
If farmers are willing to risk some of their plants being harmed, we may be able to use more aggressive methods to eradicate SLF. <br />
Is it necessary to remove SLF throughout the growing season, or only before harvesting? <br />
The current vacuum solution works only during harvesting, and would have to be adapted to other vehicles that can operate through the growing season if necessary. <br /> <br />
References <br />
 <br />
Elsensohn, Johanna E et al. “Experimental evidence supports the ability of spotted lanternfly to hitchhike on vehicle exteriors as a mechanism for anthropogenic dispersal.” Royal Society open science vol. 11,7 240493. 10 Jul. 2024, doi:10.1098/rsos.240493 <br />
https://pmc.ncbi.nlm.nih.gov/articles/PMC11285766/ <br />


![System Diagram]({{ "/assets/images/car.jpg" | relative_url }}) <br />
Figure 1: Percentages of different SLF life stages that remained on a car until maximum speed was reached


# First Prototype
## Design Documentation
### Component List
Fan Blade: 3D printed in PLA from the RPL. CAD from McMaster-Carr part 17545K61
(Aluminum Fan Blade for 3/16" Diameter Round Shaft, 2-1/2" Diameter, 10 Blades).
Fan Shaft: 3D printed in PLA from RPL. 3/16” diameter, 7” long.
Collection Box: Made from ⅛” thick wood cut in TDS and glued together using wood glue
provided in TDS. 2” x 6” x 6”. Hinge door for easy removal of SLF and flange on back
for mounting to tractor.
Cone: 3D printed in PLA from the RPL. The funnel portion is 12” tall, 6” wide, and 2” deep. The
tube portion on the back has an OD of 2”, an ID of ⅞”, and is ½” long.
Crush Box and lid: 3D printed in PLA from the RPL. Box: 2.85” x 1.875” x 6”. Lid: 1.37” x
1.88” x 6.20”.
Tube: 3D printed in PLA from the RPL. 3 parts (nozzle and 2 modular shaft parts). Nozzle: 3.4”
3.4” x 2.2”. Shaft Part: 3.40” x 3.40” x 0.8”.

### CAD
Isotropic View of CAD Model
Vertical Cross Section View
Top-down Cross Section View
Diagram Showing Function
### Assembly process
Fan and Tube: Glue the two shaft portions of the tube together by carefully applying a small
amount of superglue to the top of the raised outer ring of one part and placing the back of the
other part on top, making sure that their walls align. Next, attach the fan to the shaft by sliding
the shaft into the fan hole and applying a small amount of super glue. When both the shaft
portion of the tube and the fan and fan shaft are dry, slide an M4 washer onto the shaft and slide
the shaft into the small holes of the tube as shown in the above diagrams. Finally, attach the
nozzle portion of the tube to the rest of the tube with a small amount of superglue.

### Structure
Overall structure: Connect the collection box and the crusher box by applying a small amount of superglue around the lower edges of the crusher box and holding it on top of the collection box, ensuring the 2 side holes line up. Then, take the already-assembled fan and tube and put a ring of hot glue around the outer edge of the nozzle of the tube. Quickly place the tube into the back hole of the crushing box, making sure that the tube is not slanted and does not extend too far into the crushing box. Follow the same procedure but now with the back of the cone and the front of the crush box.

## Design Tests
### Fan Blade Durability
What you are testing?
-How long can the fan that operates the vacuum mechanism last under constant usage?
-Does it survive long enough?
How you tested it,
-Leave the device on for 20 minutes continuously.
-For this prototype, we are not testing using a motor, so we will attach our fan blade and shaft to a drill and test up to the max speed of the drill 
-We will count the number of scratches on the blade and the size of each scratch. 
What happened?
-The fan blade remained structurally intact after 20 minutes of continuous operation at high speed
-There was no cracking, or catastrophic failure of the blade (the chip was caused by the test against debris)
-There were noticeable friction marks on the shaft after the test, indicating some misalignment or not enough clearance 
-The shaft began to warp during the test
What design changes may be needed as a result:
-The next prototype should include a steel or aluminum shaft as to prevent warping and to improve the misalignment issues
-The support bearing for the rod need to be properly aligned and assembled to further improve the misalignment problems
-The next prototype should include a mechanism to better prevent axial sliding of the shaft within the tube. Shaft collars with set screws could be used to prevent axial motion without hindering rotation. 
-For the next prototype we will also need to test how our motor handles under extended use. 

### Resilience against debris
What you are testing
-Can the prototype withstand large particles or unwanted debris being vacuumed into the system?
-Does the prototype jam or clog significantly? What diameter of particle debris causes the most damage to the system (e.g nicks in the blade).
How you tested it,
-Attempt to use the device to ingest different types of small objects like paper balls, nuts, rocks, small twigs, etc.
-We will test objects from 1cm to 5cm diameter for good tolerances on the sizes of SLF and grapes.
What happened?
-It successfully ingested and passed smaller debris like dust and small wooden shavings with no issue
-Medium sized debris passed mostly with no issue, however one piece caused a chunk of one of the blades to come off 
-There was no catastrophic damage, but repeated impacts may cause long term wear and degradation
What design changes may be needed as a result:
-The blade for the next prototype should be ordered off of McMaster and be made out of a metal as opposed to PLA which will make the blade more robust and less vulnerable to damage from debris.
-Blade choice will also be re-evaluated on suction ability 
-We will also develop a filter to not allow any larger debris to even enter the section which holds the blade. 

### Support loads
What you are testing?
-Can the mounting components support the weight of the device even while the collection box is full? 
-How many grams of weight can be placed into the storage compartment before the mounting structure breaks or detaches?
How you tested it,
-Mount the prototype to a surface/jig and fill the storage container with an increasing amount of weight.
-Our final design predicted a max weight of 5 lbs, for this test we will test against a load of 1 lb 
What happened?
-We added 50g masses while only supporting the entire assembly from the mounting bracket until the total mass held within the collection chamber reached 500g (1.1 lb), which is more than it would ever need to be able to carry if it was full of SLF (adults are approximately 0.5g). 
What design changes may be needed as a result:
-No major design changes are required as the mounting bracket successfully supported 500g with zero sign of failure or detachment 
-For the final prototype we may still reinforce the bracket slightly to improve long term durability and increase the safety factor, especially when considering the motion of the tractor or harvester 

## Success Criteria
The device should be able to withstand consistent usage, successfully capture SLF-sized objects, and withstand being mounted on a tractor as it navigates the orchard:
Fans at the same rate for at least 15 minutes without a measurable decrease in power or noticeably damaging the fan. Maintaining consistent performance is a high priority.
The device does not clog or jam to the point of dysfunction when exposed to the test materials over 3 consecutive trials using test materials of 1cm to 5cm diameter. More consecutive runs are not a priority for durability.
The device should successfully remove 70% of visible SLF (or decoy bugs with added adhesive to simulate SLF claws) on a test vine in under 5 minutes of operation. Higher removal efficiency is a mid priority.
The device should keep its mounted orientation as up to 3 lbs (more than 2500 SLF, assuming an average weight of 0.5 grams, representing an upper bound of harvesting capacity ) is added to the collection box 



# Final Prototype
