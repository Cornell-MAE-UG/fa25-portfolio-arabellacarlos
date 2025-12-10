---
layout: project
title: Wrench Design Project
description: MAE 3270 Final Project
technologies: [Autodesk Fusion, ANSYS, MATLAB]
image: /assets/images/CADiso
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
Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75.<br /><br />
![Baseline design drive diagram.](/assets/images/baseDesignDriveDiagram.png "Baseline design drive diagram.")<br />
Baseline design drive diagram.<br /><br />
Additionally, we wanted our wrench to have more material around the drive so that that part of the drive was less prone to deformation. In doing so, the shape of the handle changed in width at sharp corners, so we added fillets to mitigate stress concentrations at those points. We created a design in Fusion 360 with rough dimensions, created a function in MATLAB that would find the required material properties, and filtered materials in Granta to find ones that worked. We then tweaked the CAD and code as needed to narrow down the list of materials we wanted.

My partner and I decided to use Aluminum 2424. Although price was not something that we were told to consider, we decided to factor it in to make it more realistic. Aluminum 2424 has the following properties: <br />
    -Young's Modulus: 9.86 Msi <br />
    -Poisson's Ratio: 0.333 <br />

 <br />

This is our design in CAD with key dimensions shown.
![CAD Isotropic View.](/assets/images/CADiso.png "CAD Isotropic View")<br />
Isotopic view of Wrench cad <br />
![CAD Dimensions Top.](/assets/images/CADtopProfile.jpg "CAD Dimensions Top")<br />
Top view of Wrench cad <br />
![CAD Dimensions Side.](/assets/images/CADsideProfile.jpg "CAD Dimensions Side")<br />
Side view of Wrench cad <br />

We then performed both hand calculations and FEM analysis using ANSYS to find if our design fulfilled the design requirements.

Our MATLAB code is as follows
`
%% Calculating X_s

function results=calculate(L, h, b)
disp(strcat('L:', num2str(L), ', h:', num2str(h), ', b:', num2str(b)))
M = 600; % max torque (in-lbf)
c = 1.0; % distance from center of drive to center of strain gauge
E = 9.86E6; % Young's modulus (psi)
nu = 0.333; % Poisson's ratio
su = 370.E3; % tensile strength use yield or ultimate depending on material (psi)
KIC = 15.E3; % fracture toughness (psi sqrt(in))
sfatigue = 115.e3; % fatigue strength from Granta for 10^6 cycles
k=2;

p=M/L;
s=6*M/(b*h^2);
s_0=s/10^3;
X=su/s;
disp(strcat('Max stress: ', num2str(s_0), 'psi'))
disp(strcat('X_0: ', num2str(X)));
disp(strcat('Does X_0 pass?_', num2str(X>=4)))


%% Calculating Max Displacement
I=(b*h^3)/12;
displacement=(p*L^3)/(3*E*I);
disp(strcat('Displacement: ', num2str(displacement), ' in'));

%% Calculating strain
st1=(s/E)*(L-c)/L;
st2=-st1;
st=k*(st1-st2)*(10^6)/4; % mV/V
disp(strcat('Strain: ', num2str(st), ' microstrain'));
disp(strcat('Output: ', num2str(st/1000), 'mV/V'))
disp(strcat('Does strain pass?_', num2str(st/1000>=1)))

%%Calculate factor of safety of crack growth
a = 0.04; %crack depth (in) (0.01 mm)
p=pi*(a/b)/2;
F=1.12;
Sg = 6*M/(b*h^2);
K = F*Sg*sqrt(pi*a);
Xk=KIC/K;
disp(strcat('X_k: ', num2str(Xk)));
disp(strcat('Does X_k pass?_', num2str(Xk>=2)))

%%Calculate factor of safety of fatigue stress
Xs=sfatigue*b*h^2/(6*M);
disp(strcat('X_s: ', num2str(Xs)));
disp(strcat('Does X_s pass?_', num2str(Xs>=1.5)))
disp('-----')


end
L=9.0625;
h=0.8;
b=0.5;
calculate(L, h, b)
`
