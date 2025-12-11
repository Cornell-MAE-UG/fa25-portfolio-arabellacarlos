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

![Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75.]({{ "/assets/images/baseDesignDiagram.png" | relative_url | }})
Baseline design diagram. In inches, L=16, c=1, b=0.5, h=0.75.<br /><br />
![Baseline design drive diagram.](/assets/images/baseDesignDriveDiagram.png "Baseline design drive diagram.")<br />
Baseline design drive diagram.<br /><br />
Additionally, we wanted our wrench to have more material around the drive so that that part of the drive was less prone to deformation. In doing so, the shape of the handle changed in width at sharp corners, so we added fillets to mitigate stress concentrations at those points. We created a design in Fusion 360 with rough dimensions, created a function in MATLAB that would find the required material properties, and filtered materials in Granta to find ones that worked. We then tweaked the CAD and code as needed to narrow down the list of materials we wanted.

```
function material=findMaterials(L, h, b);
disp(strcat('L:', num2str(L), ', h:', num2str(h), ', b:', num2str(b)))
M = 600; % max torque (in-lbf)
c = 1.0; % distance from center of drive to center of strain gauge
nu = 0.335; % Poisson's ratio
k=2;

X=4;
s=6*M/(b*h^2);
su = X*s;
disp(strcat('Min su:  ', num2str(su), 'psi'));

st=1;
E=k*s*(L-c)*10^3/(2*st*L);
disp(strcat('Max Youngs mod:  ', num2str(E), 'psi'));

%%Calculate factor of safety of crack growth
a = 0.04; %crack depth (in) (0.01 mm)
Xk=2;
F=1.12;
Sg = 6*M/(b*h^2);
K = F*Sg*sqrt(pi*a);
KIC=Xk*K;
disp(strcat('KIC min:  ', num2str(KIC)));

%%Calculate factor of safety of fatigue stress
Xs = 1.5;
sfatigue=Xs*(6*M)/(b*h^2);
disp(strcat('sfatigue min:  ', num2str(sfatigue)));
disp('-----')


end

findMaterials(9, 0.8, 0.5);
```

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

We then hand calculations to find if our design fulfilled the design requirements.

Our MATLAB code is as follows
```
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
```

The results we got from this are as follows:
```
>> MAEFinalHW
L:9.0625, h:0.8, b:0.5
Max stress:11.25psi
X_0:32.8889
Does X_0 pass?_1
Displacement:0.078089 in
Strain:1015.0731 microstrain
Output:1.0151mV/V
Does strain pass?_1
X_k:3.3583
Does X_k pass?_1
X_s:10.2222
Does X_s pass?_1
-----
```

We then performed FEM analysis using ANSYS to yield more accurate results. As instructed, we clamped the drive of the wrench around the four larger faces. However, we noticed that there were stress concentrations that came from clamping that part of the drive and not the entire drive, so we had another loading case where the entire drive was clamped.

![Loading Case A](/assets/images/caseALoading.jpg "Loading Case A")<br />
Loading Case A <br />
![Loading Case B](/assets/images/caseBLoading.jpg "Loading Case B")<br />
Loading Case B <br />

Arrow denotes a 66.67 lbf force.<br /><br />

As you can see in the following image, the maximum stresses occured at the edges of the drive faces that were not clamped. This is due to the sharp corners of the clamped faces being joined with the unclamped section of the drive. If we were to make this wrench, these stress concentrations would not occur because the drive would be continuous and not have these sharp corners.
![stressZoom](/assets/images/AcoarseMeshStressZoomedIn.png "stressZoom")<br />
Stress Concentrations due to Loading Case A <br />
Due to these ficticious stress concentrations, I have decided to base my analysis on loading case B, with the entire drive clamped rather than just part of it.

We also had multiple meshes with different mesh sizes. Our first mesh size was 0.1875" on the handle and 0.1" on the drive (Mesh 1). Our second mesh size was 0.125" on the handle and 0.06" on the drive (Mesh 2). Our final mesh size was 0.075" on the handle and 0.03" on the drive (Mesh 3).

Our displacements for loading case A mesh size 1 was as follows.
![DeformationCoarseMesh](/assets/images/CoarseMeshDeformations.png "DeformationCoarseMesh")<br />
![DeformationFineMesh1](/assets/images/FineMesh1Deformation.png "DeformationFineMesh1")<br />
![DeformationFineMesh2](/assets/images/FineMesh2Deformation.png "DeformationFineMesh2")<br />



These are the strain values experienced at the location of the gauge for meshes 1, 2, and 3 for loading case B.
![StrainCoarseMesh](/assets/images/strainCoarseMesh.PNG "StrainCoarseMesh")<br />
![StrainFineMesh1](/assets/images/strainFineMesh1.PNG "StrainFineMesh1")<br />
![StrainFineMesh2](/assets/images/strainFineMesh2.PNG "StrainFineMesh2")<br />

As we can see with the finest mesh size, the value of the voltage output due to strain would be 

