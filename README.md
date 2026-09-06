# CSF Infusion Study Calculator ($R_{out}$, Curve Fitting & Differential Analysis)

An interactive neurosurgical clinical tool for recording **time intervals and intracranial pressure (ICP)** during constant-rate lumbar infusion tests, fitting smooth continuous pressure curves $P(t)$, computing the **first and second derivatives**, and marking the **plateau pressure arrival** across all graphs.

Developed by **Dr G Narenthiran FRCS(SN)**.


> ⚠️ **Disclaimer:** The CSF-infusion calculator should not be used for clinical purposes and the user should verify the calculations.

---


## 🔬 Clinical Principles & Mathematical Models

### 1. Recorded Data, Curve Fitting & Plateau Pressure ($P_p$)
Discrete clinical measurements of time ($t$ in minutes) and ICP ($P$ in mmHg) are recorded during the infusion:
- **Baseline Phase ($P_0$ / $P_{op}$)**: Initial resting pressure prior to volume loading.
- **Ramp Phase**: Dynamic pressure elevation during constant infusion at rate $I_c$ (typically 1.0 or 1.5 mL/min).
- **Plateau Phase ($P_p$)**: Equilibrium state where infusion rate equals CSF absorption rate. The moment $t_{plateau}$ where plateau pressure is attained is visually identified and marked across all three curves.

A continuous polynomial regression curve $P(t)$ is fitted across the empirical data points:
$$P(t) = c_0 + c_1 t + c_2 t^2 + c_3 t^3 + c_4 t^4$$

---

### 2. First Derivative: Rate of Pressure Change ($\frac{dP}{dt}$)
The first derivative represents the **instantaneous rate of ICP rise** (velocity in mmHg/min):
$$P'(t) = \frac{dP}{dt} = c_1 + 2 c_2 t + 3 c_3 t^2 + 4 c_4 t^3$$

- **Clinical Significance**: Indicates instantaneous compliance strain. The peak of $\frac{dP}{dt}$ identifies the steepest slope of pressure rise where intracranial elastance is most acutely challenged.
- **Plateau Marker**: As the plateau is reached, $\frac{dP}{dt} \to 0$ (velocity decelerates to zero). Marked with a vertical reference line and red indicator.

---

### 3. Second Derivative: Acceleration of Pressure Rise ($\frac{d^2P}{dt^2}$)
The second derivative represents the **curvature and acceleration** of the pressure response (mmHg/min²):
$$P''(t) = \frac{d^2P}{dt^2} = 2 c_2 + 6 c_3 t + 12 c_4 t^2$$

- **Clinical Significance**: 
  - The zero-crossing point where $\frac{d^2P}{dt^2} = 0$ corresponds to the **inflection point** of the infusion curve.
  - Prior to this point ($\frac{d^2P}{dt^2} > 0$), pressure is accelerating upwards.
  - Beyond this point ($\frac{d^2P}{dt^2} < 0$), compensatory CSF resorption pathways activate, decelerating pressure rise toward the plateau.
- **Plateau Marker**: At steady plateau, both acceleration and velocity flatten out.

---

### 4. Resistance to CSF Outflow ($R_{out}$)
$$\Delta P = P_{plateau} - P_{baseline}$$

$$R_{out} = \frac{P_{plateau} - P_{baseline}}{I_c} \quad [\text{mmHg}/(\text{mL}/\text{min})]$$

$$C_{out} = \frac{1}{R_{out}} \quad [(\text{mL}/\text{min})/\text{mmHg}]$$

| $R_{out}$ Value | Clinical Interpretation | Recommendation |
|---|---|---|
| **$< 10 \text{ mmHg}/(\text{mL}/\text{min})$** | **Normal** | Low probability of shunt benefit based on resistance alone. |
| **$10 - 12 \text{ mmHg}/(\text{mL}/\text{min})$** | **Borderline** | Equivocal; correlate with clinical tap test and DESH neuroimaging. |
| **$> 12 \text{ mmHg}/(\text{mL}/\text{min})$** | **Pathological** | Impaired resorption; statistically favorable candidate for shunt diversion. |

---

## ⚡ Key Features
- **Editable Clinical Recording Table**: Add, edit, or remove time intervals ($t$) and measured ICP values.
- **Customizable ICP Safety Threshold**: Input field with default set to 30 mmHg, rendered as an actionable red dashed threshold line across Graph 1.
- **Three Linked Scientific Visualizations with Plateau Markings**:
  1. **Graph 1**: Discrete ICP measurements with overlaid polynomial curve fit $P(t)$ and **🚩 Plateau Reached Point** ($P_p$, $t_{plateau}$).
  2. **Graph 2 (1st Derivative)**: Instantaneous rate of pressure rise $\frac{dP}{dt}$ (mmHg/min) with peak slope marker and **🚩 Plateau Arrival Indicator** ($\frac{dP}{dt} \to 0$).
  3. **Graph 3 (2nd Derivative)**: Pressure acceleration $\frac{d^2P}{dt^2}$ (mmHg/min²) identifying the inflection point and **🚩 Plateau Arrival Indicator**.
- **Synchronized Plateau Reference Lines**: Prominent vertical dashed lines and callout badges spanning all three graphs at the exact minute where plateau equilibrium is achieved.
- **Hydrodynamic Metrics Dashboard**: Real-time calculation of $R_{out}$, $\Delta P$, $C_{out}$, and peak $\frac{dP}{dt}$.
- **Comprehensive Documentation Generator**: One-click summary formatted for Electronic Patient Records (EHR) with table export, copy to clipboard, print/PDF, and email.
- **Dark and Light Theme Support**.

---

## 👨‍⚕️ Author & Attribution
- **Author**: © Dr G Narenthiran MB ChB BSc(MedSci)(Hons)FEBNS FRCS(SN), 2026; `g_narenthiran@hotmail.com`
- **Developed by**: Dr G Narenthiran FRCS(SN), Neurosurgery Research Listserv, UK; `g_narenthiran@hotmail.com`
- **Dedication**: *Dedicated to my mother Mrs Nirmaladevy Ganesalingam BSc*

---

## 📚 Key References
1. Katzman R, Hussey F. A simple constant-infusion manometric test for measurement of CSF absorption. *Neurology* 1970;20(6):534-544.
2. Marmarou A, Shulman K, Rosende RM. A nonlinear analysis of the cerebrospinal fluid system and intracranial pressure. *J Neurosurg* 1978;48(3):332-344.
3. Czosnyka M, Czosnyka Z, Momjian S, Pickard JD. Cerebrospinal fluid dynamics. *Physiol Meas* 2004;25(5):R51-R76.
4. Boon AJ, Tans JT, Delwel EJ, et al. Dutch normal-pressure hydrocephalus study: prediction of outcome after shunting by resistance to outflow of cerebrospinal fluid. *J Neurosurg* 1997;87(5):687-693.
