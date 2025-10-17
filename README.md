# -RISC-V-SoC-Program_week_4
<details>
  <summary>NgspiceSky130 - Day 1 - Basics of NMOS Drain current (Id) vs Drain-to-source Voltage (Vds)</summary>
  <h2>Introduction to Circuit Design and SPICE simulations</h2>
  <p>This document introduces the basics of circuit design and the importance of SPICE simulations using the Sky130 PDK.
It helps in understanding the behavior of an NMOS transistor, its current–voltage relationship (Id–Vds), and how the transistor operates in different regions (resistive and saturation).</p>
<p>SPICE (Simulation Program with Integrated Circuit Emphasis) is a powerful tool that allows circuit designers to simulate and verify the functionality of circuits before fabrication. By running SPICE simulations, we can analyze transistor-level parameters such as current, voltage, and power for different biasing conditions, which helps to ensure performance and reliability of IC designs.</p>
  <p>Key points to understand before simulation :
  <ul>
    <li>SPICE simulations replicate real transistor behavior through mathematical models.</li>
    <li>The Sky130 PDK provides the model files and parameters needed for realistic device simulation.</li>
    <li>Simulations allow us to visualize Id–Vds characteristics, which reveal how a transistor switches between linear and saturation regions.</li>
  </ul></p>
  <p><ol><li> Threshold Voltage (Vth)</li>
    <p>The Threshold Voltage (Vth) is the minimum Gate-to-Source voltage (Vgs) required to form a conductive channel between the source and drain terminals.
When Vgs < Vth,the transistor is OFF (cut-off region).
When Vgs > Vth, the device turns ON, forming an inversion layer that allows current to flow.</p>
  <p><b>Understanding Channel Formation:</b></p>
  <p><ul><li>At small Vgs: No inversion channel, the transistor remains off.</li>
<li>As Vgs increases: Positive gate voltage repels holes in the p-type substrate and attracts electrons near the interface, forming a depletion region.</li>
<li>At Vgs = Vth: A strong inversion layer forms, creating a conductive channel.</li>
<li>At Vgs > Vth: The channel becomes stronger and current flows from Drain → Source depending on Vds.</li></ul></p>
  <li><b>Effect of Substrate Bias (Vsb)</b></li>
<p>When a voltage is applied between the Source and Bulk (Vsb), it modifies the threshold voltage. This phenomenon is known as the Body Effect or Substrate Bias Effect.</p>
  <p><ul><li>When Vsb > 0, the depletion region widens.</li>
<li>The threshold voltage increases, requiring a higher Vgs to turn the device ON.</li>
  <li>The relationship can be expressed as:</li></ul></p>
  <p allign="center"><img alt="image" src="https://github.com/user-attachments/assets/1d5e2c79-301d-4652-ba75-3984ec53c945" /></p>
  Where
  <p><ul><li>V<sub>to</sub> = threshold voltage at 𝑉 <sub>𝑆𝐵</sub>= 0 </li>
<li>γ = body effect coefficient</li>
<li>𝜙<sub>𝐹</sub>= Fermi potential</li></ul></p>
  Thus, applying a positive substrate potential increases 𝑉<sub>𝑡ℎ</sub> and reduces current for the same 𝑉<sub>𝑔𝑠</sub></ol></p>
  <h2>NMOS resistive region and saturation region of operation</h2>
  <p>An NMOS transistor is a four-terminal device with Gate (G), Source (S), Drain (D), and Bulk (B) terminals.
When a positive gate-to-source voltage (Vgs) is applied, it induces an electric field in the channel region that attracts electrons, forming a conductive n-channel between source and drain.</p>
  <p>The transistor can operate in different regions depending on the applied voltages Vgs and Vds.<br>
  <ol>
    <p><li><b>Resistive (Linear) Region</b></li></p>
    <p>When the NMOS transistor behaves like a variable resistor, it is said to operate in the resistive or linear region.</p>
    <b>Condition :</b>
      <p align="center"><img alt="image" src="https://github.com/user-attachments/assets/cb059dde-a3d7-412c-8433-945ea8bd6df0" /></p>
    <p><ul>
      <li>A conductive channel is formed between source and drain.</li>
<li>The current increases almost linearly with Vds.</li>
<li>The transistor behaves like a voltage-controlled resistor.</li></ul></p>
    <b>Drain Current Equation (Linear Region) :</b>
    <p align="center"><img width="543" height="84" alt="image" src="https://github.com/user-attachments/assets/38cbcd78-45a4-49c9-889c-a05343a1152b" /></p>
    <p><b>Where :</b></p>
    <p>
      <ul><li><p>μ<sub>n</sub>: Electron mobility</p></li>
	      <li><p>𝐶<sub>ox</sub>: Gate oxide capacitance per unit area</p></li>
        <li><p>W , 𝐿 : Transistor width and length</p></li>
        As Vds increases, the current initially rises linearly, indicating resistive behavior.​
      </ul>
    </p>
    <p><b>Practical Understanding:</b></p>
    <p><ul>
      <li>In digital circuits, NMOS transistors are usually operated in the saturation region (as switches).</li>
<li>In analog circuits, both linear and saturation regions are used depending on the design.</li>
    </ul></p><h2></h2>
    <p><li><b>Saturation (Active) Region</b></li></p>
    <p>When Vds becomes large enough, the channel near the drain end gets pinched off, and the NMOS enters saturation (or active) region.</p>
    <b>Condition :</b>
    <p align="center"><img alt="image" src="https://github.com/user-attachments/assets/f43fba4d-49a0-45a0-85da-4190b64d3409" /></p>
    <p><ul>
      <li>The current saturates and becomes almost independent of Vds.</li>
<li>The NMOS acts as a current source controlled by Vgs.</li></ul></p>
    <b>Drain Current Equation (Saturation Region) :</b>
    <p align="center"><img width="534" height="82" alt="image" src="https://github.com/user-attachments/assets/2adbddc8-c966-4955-8f55-ffc5052314fe" /></p>
    where 𝜆 is the channel length modulation parameter.
    <p><b>Observation :</b></p>
    <p><ul>
      <li>For higher gate voltages (Vgs), the drain current (Id) increases quadratically.</li>
<li>The slope of the saturation curve slightly increases due to channel length modulation (𝜆).</li></ul></p>
    <b>Practical Understanding:</b>
    <p><ul>
      <li>In digital circuits, NMOS transistors are usually operated in the saturation region (as switches).</li>
<li>In analog circuits, both linear and saturation regions are used depending on the design.</li></ul></p><h2></h2>
    <p><li><b>Visualization of Id–Vds Curves</b></li></p>
    <p>In SPICE simulations, the Id–Vds curve is generated by sweeping the drain-to-source voltage (Vds) for multiple gate voltages (Vgs).</p>
    <p><ul><li>For small Vds, the curve is linear (resistive region).</li>
<li>For larger Vds, it flattens out (saturation region).</li>
<li>Increasing Vgs shifts the curve upward, indicating higher current levels.</li></ul></p>
  </ol>
  </p>
  <h2>Introduction to SPICE</h2>
</details>
<details>
  <summary> NgspiceSky130 - Day 2 - Velocity saturation and basics of CMOS inverter VTC</summary>
  <h3>SPICE simulation for lower nodes and velocity saturation effect</h3>
  <h3>CMOS voltage transfer characteristics (VTC)</h3>
</details>
<details>
  <summary>NgspiceSky130 - Day 3 - CMOS Switching threshold and dynamic simulations</summary>
  <h3>Voltage transfer characteristics – SPICE simulations</h3>
  <h3>Static behavior evaluation – CMOS inverter robustness – Switching Threshold</h3>
</details>
<details>
  <summary>NgspiceSky130 - Day 4 - CMOS Noise Margin robustness evaluation</summary>
  <h3>Static behavior evaluation – CMOS inverter robustness – Noise margin</h3>
</details>
<details>
  <summary>NgspiceSky130 - Day 5 - CMOS power supply and device variation robustness evaluation</summary>
  <h3>Static behavior evaluation – CMOS inverter robustness – Power supply variation</h3>
  <h3>Static behavior evaluation – CMOS inverter robustness – Device variation</h3>
</details>
