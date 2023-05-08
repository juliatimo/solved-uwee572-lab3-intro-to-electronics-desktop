Download Link: https://assignmentchef.com/product/solved-uwee572-lab3-intro-to-electronics-desktop
<br>
ANSYS Electronics Desktop (ED) is a powerful microwave circuit design package from ANSYS.  Many RF/microwave companies use either ADS from Keysight, CST or Desktop from ANSYS to design microwave devices and systems.

The purpose of this HW is to become familiar with Electronics Desktop (ED) using both ideal and physical TL models.  The TL circuits can be simulated using two techniques. They are circuit model and electromagnetic (EM) model.  The circuit simulation is similar to SPICE and MultiSim.  It is based on the lumped elements and ideal TL with corrections to mitigate the TL discontinuities. EM model uses the circuit layout (physical dimension). EM simulation is accurate but it is much slower than the circuit simulations.  In this HW we are using the circuit simulations.  The EM simulations will be used in other assignments.

<strong>Objectives:</strong>

(1)To become familiar with ED microwave design software.

(2)To simulate the reflection from an unmatched TL using ideal TL model

(3)To simulate the transmission through an unmatched TL using ideal TL model

(4)To simulate the physical TL models

<strong>Designer training program:</strong>

The ED training programs (compressed) are on the class web site.

ED Ideal TL

ED Physical TL 25

<strong>PCB substrate: (All circuit designs in this class will use Duroid </strong>

<strong>5870)</strong>

Duroid 5870, <sub>r</sub>=2.33 – <em>j</em>0.0028, d=1.57mm (62 mil)

<strong>References:</strong>

Desktop tutorial files

<ol>

 <li><strong>Simulations using ideal TL</strong></li>

</ol>

<strong>II-1. Reflection from an unmatched TL using ideal TL model at 2.4 GHz</strong>

This model uses only one port (Port1) and measures S11.

The simplest way to describe microwave circuits is the ideal TL model.  TLs are specified in terms of the characteristic impedance Zo and phase shift (length) at the designed frequency.  The discontinuities such as TL step and tee are not included.  The ideal TL model is for training purpose and you are not using it in your design.

The example “Ideal TL R25” contains the quarter-wave (/4) matching circuit which matches 25 ohm load to 50 ohm TL.  The TL length in terms of phase shift is specified at 3 GHz.  Open the file and become familiar with this.

The quarter wave TL section (value of Z<sub>1</sub>) is given by

Z<sub>1</sub>=SQRT(Z<sub>o</sub>*R<sub>L</sub>)

R<sub>L</sub>=25 ohm, Z<sub>o</sub>=50 ohm

Fig.1: Ideal TL model

-Start  ED.

-Open the project file  Ideal TL R25.adsn

-File &gt; Open&gt; (find the file)

Use View &gt; Windows Layouts &gt; Default to combine all windows.

-Make sure Duroid 5870 is specified (Project Manager &gt;Nexxim1&gt;Data)

We will use Duroid 5870 for all projects.

-Check

Nexxim1 &gt; Data

Ports

Analysis Results

Set Z<sub>1</sub>=35 ohm.

-Change the frequency span to 1 to 6 GHz and plot results.

Does the frequency of S11 min occur at 3 GHz?

-Change the TL length of Z<sub>1</sub> to 180 deg and check the results.

Does the frequency of S11 min change?

-Change the load resistor to 100 ohm and design a new /4 TL (find the value of Z<sub>1</sub>).

Note: See Appendix I to do analysis and plot results.

<strong>To create the above circuit, you can use </strong>From Components:

To create transmission lines Ideal distributed

TRLE.NX TL Electrical Length

Resistor (ideal)

RES

Ground:  from the top list

Port: from the top list Connect all items <strong>Ideal distributed</strong>

<table width="345">

 <tbody>

  <tr>

   <td width="240">Ideal OPEN: NXOSTE,</td>

   <td width="105">Ideal Open</td>

  </tr>

  <tr>

   <td width="240">Ideal TL:             TRLE_NX, TL</td>

   <td width="105">Electrical length</td>

  </tr>

 </tbody>

</table>




Fig.*: Another example of the ideal TL model

<strong>II-2. Transmission through an unmatched TL using ideal TL model at 2.4 GHz</strong>

This model uses two ports (Port1 and Port2) and measures S11 and S21

The unmatched TL has 50, 100 and 50 ohm sections as shown below.  We want to set S11=0  (|S21|=1) at 2.4 GHz.   Find the length of the 100 ohm TL section.  The length of 50 ohm sections are not important.

Set the 50 ohm sections to 0.2 wavelength at 2.4 GHz.

Fig*: Unmatched TLs Create the ED model using Port1 and Port2.

Set the frequency range to 1-6 GHz.

Simulate the transmission (S21).

Simulate the transmission (S11).

What is the value of S21 when S11 is minimum?  What is the effective length (in terms of wavelength) of the 100 ohm section when S11 becomes minimum?

Fig*: Ideal TL model: Cascaded TLs

Fig.*: S11 and S21responses

<ul>

 <li><strong>Simulation using the physical TLs</strong></li>

</ul>

<strong>III-1. Physical microstrip TL characteristics</strong>

Note: The designed frequency is 3 GHz in this example.

The actual microwave circuits cannot be described by ideal TLs.    The physical TL is specified by the width and length.  For a given Z<sub>o</sub>, we need to obtain the TL width and effective dielectric constant which determined the physical TL length.

Start: Circuit &gt; TRL &gt;Microstrip &gt;Single &gt;Duroid5870

-Duroid 5870 must have Substrate Duroid 5870 H=62 mil (1.57mm )

HU=                  (not required)

ER=2.33             (dielectric constant)

TAND=0.0012              (loss tangent)

To find the 50 ohm TL dimension, enter these values

Z<sub>o</sub>=50                              (characteristic impedance)

E=90    (not required) Synthesis 3 GHz

Press “Synthesis”

-Read details

W=4.49mm     (TL width) Keff= 1.9713           (Effective dielectric constant)

-Repeat the same procedure to calculate W and Keff of other TL sections.

<strong>Fig.*: TRL window to design microstrip TL.  Frequency is 1 GHz, d=1.52mm.</strong>

<strong>III-2. Reflection from an unmatched TL using physical TL model at 2.4 GHz</strong>

***Tutorial file name: Physical TL R25-v6.adsn

Ideal RL is replaced by a 25  chip resistor.

Ideal TLs are replaced by microstrip TLs. Step is needed to connect two TLs.

Using the TL model obtained in II-1, you will design a new quarter wave matching circuit which is based on the physical TL dimension.

-Delete 25ohm load and TLs from the ideal TL example.

-Add a physical TL using

Components &gt; Distributed &gt; Microstrip &gt; Transmission Lines MS TRL: Trans. Line physical length

(All devices will be shown if you click “<strong>Components</strong>” on the left bottom)

-Add a chip resistor

Resistors &gt;NXCHIPRES: Chip resistor

-Use “MS STEP” to include the effects of the TL width change.  Distributed &gt; Microstrip &gt; General components &gt; MS Step

The new circuit will be

Fig.*: Physical TL model

-Analyze it and check the S11 response.  The frequency of S11 min is no longer at 2.4 GH.

-Adjust the TL length of the quarter wave section so that S11 min occurs at 2.4 GHz (designed frequency).

-If the results are good, print the circuit diagram, layout, and S11 response (dB). Circuit &gt; Layout Editor

Draw &gt; Align MW ports

You may need to set “D” (displacement) in MS STEP to adjust the TL position.

The layout is shown below.  Move a resistor out of the microstrip TL.

Fig.*: Physical TL layout

<strong>III-3. Transmission through an unmatched TL using physical TL model</strong>

The unmatched TL measured in Lab1 is shown below. You will be simulating this PCB in the frequency domain.   Create a physical TL model to simulate this circuit.  The 100 ohm center TL is 100 mm.

Fig.*: Test PCB from TDR1 lab




Fig.*: Example of a physical TL model




Fig.*: S11 and S21 responses of a physical TL model

-Analyze it and check the S11 and S21 responses.

-At what frequency S21 becomes maximum.

-If we want to set S21 max frequency to 2.4 GHz, what should be the length of the center TL?

-If the results are good, print the circuit diagram, layout, and S11 and S21 responses (dB).

Circuit &gt; Layout Editor

Draw &gt; Align MW ports

You may need to set “D” (displacement) in MS STEP to adjust the TL position.

<strong>Calculate the expected S11 and S21 using the layered structured model and compare it with the simulations.  See Appendix II.</strong>




<h1>Appendix I</h1>

<h2>(1) Analysis</h2>

Right click “Analysis (in Project manager)”.

You will see “Add analysis Nexxium solution setup &gt;Linear network analysis”.

Press Add

Enter Start, Stop, Step and press Add then OK




Right click Analysis then choose “Analyze”.

If something is wrong, the error message will be shown in the bottom window.

<h2>(2) Plot results</h2>

Go to “Results” and right click it.  Choose “Create standard report &gt; Rectangular plot”.

Lab 1 involves the reflection (S11) case.  Choose S11 mag in dB and add it.

This is the S11 plot of the simple model.

<h2>To make a copy of Ansoft screen/data</h2>

Then right click your mouse. You will see Copy to Clipboard in some cases.  Then use Copy and Paste into Word file.  PC has MS Word.

<strong>To capture the whole screen</strong>

Press PRINT SCREEN key. Use Paste to copy it in Word.

<h1>To capture the active screen</h1>

Press Alt-PRINT SCREEN key. Use Paste to copy it in Word.




<strong>Appendix II:  Layered structure model</strong>

<strong>From LN Dielectric constant transmission technique</strong>

Ref: Nicolson-Ross Method  HP Tech Note 8510-3

Let assume we have two unknowns given by <em>ε</em><em>r</em>=<em>ε ‘</em>−<em>jε </em>” and <em><sup>μ</sup></em><em>r</em><sup>=<em>μ’</em>− <em>jμ </em>” </sup>.  Fortunately, there is a simple analytical solution to obtain <sub>r</sub> and <sub>r</sub> from the measured reflection and transmission coefficients.  Unfortunately, this solution becomes unstable at certain frequencies and results are useless.  In this section, we will formulate the same TL problem using the different approach then obtain the analytical solution for <sub>r</sub> and <sub>r</sub>.

Assume the sample holder is a coaxial TL

We express the total voltage and current in each section as

[<em>V </em>1=<em>V </em><em>in</em><em>e</em>−<em>jγ</em>0 <em>ℓ</em>+<em>V</em>−1 <em>e </em><em>jγ</em>0 <em>ℓ </em>¿]¿¿¿

¿

[<em>V</em>2=<em>V</em>+2 <em>e</em>−<em>jγ</em>1 <em>ℓ</em>+<em>V</em>−2 <em>e</em><em>jγ</em>1<em>ℓ </em>¿]¿¿¿

¿

[<em>V</em>3=<em>V</em>+3<em>e</em>−<em>jγ</em><sup>0 </sup>( <em>ℓ</em>−<em>d</em><sup>) </sup><sup>¿</sup>]<sub>¿¿¿</sub>

¿

Define                    <em>Z</em><em>s</em>+<em>Z</em>0               , 1 <em>Z</em>0 <em>Z</em><em>s</em>

<em>T</em><sub>=</sub><em>e</em>−<em>jβd</em>

<table>

 <tbody>

  <tr>

   <td>[</td>

  </tr>

 </tbody>

</table>

1+<em>Γ</em>1<em>e</em>−2 <em>jβd                  </em><u>1−<em>ΓT</em></u>2

<em>Z</em>12=<em>Z</em><em>s</em>1−<em>Γ</em><sub>1</sub><em>e</em>−2 <em>jβd </em>]=<em>Z</em><em>s</em>[1+<em>ΓT</em>2 ]

<em>Z<sub>s </sub></em><u>1</u>−<em><u>ΓT</u></em><sup>2</sup>

−1

<em>Z</em><u><sub>12</sub></u>−<em>Z</em><u><sub>0 </sub></u><em>Z</em><sub>0 </sub>[1+<em>ΓT</em><sup>2 </sup>]

<em>S</em>11=<em>Z</em>12+<em>Z</em>0 =<em>Z</em><em>s </em><u>1</u>−<em><u>ΓT</u></em>2

<em>Z</em>0 [1+<em>ΓT</em>2 ]+1

1+<em>Γ </em>1−<em>ΓT</em><sup>2 </sup>( )−1

=

(<u>1+<em>Γ </em></u>)(<u>1−<em>ΓT</em></u>2<sup>2</sup>)+1                       (<em>ZZ</em>0<em>s </em>=1<u>1</u>−<u>+<em>Γ</em></u><em>Γ </em>)

1−<em>Γ </em>1+<em>ΓT                            </em>,

Then we can find the reflection coefficient of the layered structure as

<em>S</em>11=<em><u>Γ</u></em>1−(<u>1</u><em>Γ</em>−2<em><u>T</u>T</em>22)

This is the same as <sub>in</sub> which is obtained in the previous section.

Now we consider the transmission case

<em>V</em>

<em>V</em>

<em>V</em><sub>3</sub>


<em>V</em>2+<em>e</em>− <em>jβd </em>=1+<em>Γ</em>1=1−<em>Γ</em>

<em>V </em><sub>3</sub>


=(1−<em>Γ </em>)<em>T                                                </em><sup>+</sup>

or  <em><sup>V </sup></em><sup>+</sup><sub>2                            </sub>                                   <em><sup>V</sup></em>2 is defined at <em>x</em>=0

Transmitted wave into 2 <em>V</em><sub>2</sub>

<em>V</em>+<sub>1 </sub>=1+<em>Γ</em>12=1+<em>S</em>11

<em>V</em>2++<em>V</em>−2 <em>V</em>+2                     <em>V</em>−2

= + = + (1+ <sub>+</sub>)                <em>V</em>1                 <em>V</em>1                 <em>V</em>2

<em>V</em>+<sub>2</sub>1

<h1><em>V             </em>+1=(1+<em><sup>S</sup></em>11)         <em>V</em>−2 )</h1>

<h2>1+</h2>

<em>V</em>+<sub>2 </sub>also at <em>x</em>=<em>d</em>

<em>V</em>−2 <em>e</em>+ <em>jβd </em><em>Z</em>0−<em>Z</em><em>s</em>

= =−<em>Γ</em>

<em><sup>V</sup></em><sub>2</sub>+<em>e</em>− <em>jβd </em><em>Z</em><sub>0</sub>+<em>Z<sub>s</sub></em>

<em>V</em>−2+               <em>ΓT</em>2

=−

<em>V</em><sub>1</sub>

<em>V</em>2+                                  1

<em>V</em>1+=(1+<em>S</em>11)(1−<em>ΓT</em>2 )

<em>V</em><sub>3</sub>+         1 <em>V</em>1+=(1+<em>S</em>11)(1−<em>ΓT</em>2 )(1−<em>Γ </em>)<em>T</em>

<em><u>Γ </u></em>(<u>1</u>−<em><u>T</u></em><sup>2</sup>) <em><u>T </u></em>(<u>1</u>−<em><u>Γ </u></em>)

=1+         <sub>2 2 </sub>)(    2 )

1−<em>Γ T         </em>1−<em>ΓT</em>

<em><u>T </u></em>(<u>1</u>−<em><u>Γ</u></em><sup>2</sup>)

<sup>¿</sup>1−<em>Γ</em>2<em>T</em>2

Here the reflection coefficient <em>Γ</em> and the variable T are defined as

<em>Γ</em>=<em>Z</em><em>s</em>−<em>Z</em>0=√<em>ε</em><em>r</em>

<em>Z<sub>s</sub></em>

<em>T</em><em><sup>r </sup></em><em>d</em>

In summary, we obtain the same results as

<em>V</em>−<sub>1                      </sub>

<em><sup>S</sup></em><sup>11</sup><sup>=<em>V </em></sup><em><sub>in </sub></em><sup>=               </sup>1−<em>T</em><sup>2</sup><em>Γ</em><sup>2               </sup>cal. plane is at <em>ℓ</em>=0∧<em>ℓ</em>=<em>d</em>

<em>V</em><sup>+</sup><sub>3      </sub>(<u>1</u>−<em><u>Γ</u></em><sup>2</sup>)<em><u>T</u></em>

<em>S</em>21=<em>V </em><em>in</em>=1−<em>T</em>2<em>Γ</em>2

<em><sup>Γ</sup></em> &amp; T are related to <em><sup>ε</sup></em><em>r</em> &amp; <em><sup>μ</sup></em><em>r</em>                      4 unknowns