---
layout: project
title: Wrench Design Project
description: MAE 3270 Final Project
technologies: [Autodesk Fusion, ANSYS, MATLAB]
image: /assets/images/radio-machine-cad.jpg
---

For the final project of MAE 3270: Mechanics of Materials, we had to design a wrench that fulfilled the following requirements:  <br />
    -Attain at least 1.0 mV/V output at the rated torque of 600 in-lbf. <br />
    -safety factor of 4 against yield <br />
    -safety factor of 2 for crack growth from an assumed crack of depth 0.04 inches (1 mm). <br />
    -fatigue stress safety factor of 1.5 <br />
    -material must be a steel, aluminum or titanium alloy <br />
 <br />
The class was given a base design to work off of that fulfilled all requirements besides the required voltage output. Below is the baseline design given to us.

![Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75.](/assets/images/baseDesignDiagram.png "Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75." )
Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75.<br />
![Baseline design drive diagram.](/assets/images/baseDesignDriveDiagram.png "Baseline design drive diagram.")
Baseline design drive diagram.<br />
Additionally, we wanted our wrench to have more material around the drive so that that part of the drive was less prone to deformation. In doing so, the shape of the handle changed in width at sharp corners, so we added fillets to mitigate stress concentrations at those points. We created a design in Fusion 360 with rough dimensions, created a function in MATLAB that would find the required material properties, and filtered materials in Granta to find ones that worked. We then tweaked the CAD and code as needed to narrow down the list of materials we wanted.

My partner and I decided to use Aluminum 2424. Although price was not something that we were told to consider, we decided to factor it in to make it more realistic. Aluminum 2424 has the following properties: <br />
    -Young's Modulus: 9.86 Msi <br />
    -Poisson's Ratio: 0.333 <br />

 <br />
I was inspired by this old radio when I made this rendering:



Aenean tincidunt aliquam arcu, in euismod dui dapibus eu. In placerat, mi et ultrices consequat, quam ligula cursus mauris, in semper neque nibh at est. Maecenas hendrerit dignissim porta. Phasellus nec fringilla dolor. Etiam efficitur nisi sit amet velit pharetra feugiat. Etiam ultrices turpis at leo semper, eleifend scelerisque neque malesuada. Aliquam molestie congue rhoncus. Donec blandit neque dolor, nec tristique mi pretium ac. Mauris tincidunt ullamcorper magna, nec pellentesque mi sagittis quis.

Aenean tincidunt aliquam arcu, in euismod dui dapibus eu. In placerat, mi et ultrices consequat, quam ligula cursus mauris, in semper neque nibh at est. Maecenas hendrerit dignissim porta. Phasellus nec fringilla dolor. Etiam efficitur nisi sit amet velit pharetra feugiat. Etiam ultrices turpis at leo semper, eleifend scelerisque neque malesuada. Aliquam molestie congue rhoncus. Donec blandit neque dolor, nec tristique mi pretium ac. Mauris tincidunt ullamcorper magna, nec pellentesque mi sagittis quis.
