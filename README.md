Technical Note: Capacitor Energy-Driven Frequency Stabilization in GFIs

Authors: Hassan Hade

Abstract

This research presents a phase angle control formulation for Grid-Forming Inverters (GFIs) connected to photovoltaic solar systems. The proposed formulation aims to mitigate the impact of DC-link Voltage ($V_{dc}$) ripples by directly linking the squared voltage variations To the instantaneous phase angle of the inverter ($\theta_{t}$). The equation relies on calculating an integral function of the energy Deficit or surplus between the AC output and the PV input, utilizing a Ripple compensation gain measured in ($rad/V^2$). The analytical study Demonstrates that this dynamic coupling provides the inverter with a Response that emulates physical inertia behaviour, where perturbations Occurring in the capacitor energy are transformed into an angular Correction. This ensures the inverter continuously forms the grid and Supports its stability under varying operating conditions of loads and Solar irradiance.

Introduction

Grid-Forming Inverters (GFIs) play an essential role in supporting the Stability of low-inertia power systems. However, continuous Fluctuations in photovoltaic generation power ($P_{pv}$) and load Variations on the grid side ($P_{out}$) impose dynamic challenges, Including the emergence of ripples in the DC-link voltage ($V_{dc}$), Which impacts system stability. Accordingly, this research employs a control algorithm to determine The instantaneous phase angle of the inverter ($\theta_{t}$). This mechanism Is based on calculating the energy balance within the DC-link Capacitor via the integration of the instantaneous power deficit or Surplus, calculated as the difference between the exported power ($P_{out}$) and the harvested power ($P_{pv}$), combined with a ripple compensation gain ($K_{r}$). This formulation allows the inverter to Operate as a synchronous voltage source that links energy variations And squared voltage deviations to phase angle adjustments, thereby Enhancing the GFI's capability to regulate frequency and stabilize the Grid by utilizing the DC-link's dynamic energy buffer. Furthermore, The DC-link capacitor can be integrated with a battery energy storage System via a DC-DC converter to manage power flows and provide Balanced and stable electrical energy to the grid, while protecting the Capacitor and system components from electrical stress or damage Caused by sudden charging and discharging spikes.

Methodology

The electrical potential energy ($E$) stored in a capacitor is physically Defined as:

$$E=\frac{1}{2}C_{dc}V_{dc}^{2}$$

Any change in stored energy due to a power imbalance directly results In a variation in the squared voltage of the capacitor:

$$\Delta E=\frac{1}{2}C_{dc}\Delta V_{dc}^{2}$$

Since the net energy variation ($\Delta E$) is the time-integral of the Instantaneous power difference :

$$\int_{0}^{t}\Delta Pd\tau=\frac{1}{2}C_{dc}\Delta V_{dc}^{2}$$

$$2\cdot\int_{0}^{t}\Delta Pd\tau=C_{dc}\Delta V_{dc}^{2}$$

The squared voltage deviation is isolated to utilize the capacitor's Energy surplus or deficit as a direct metric for phase angle adjustment

$$\frac{2}{C_{dc}}\cdot\int_{0}^{t}\Delta Pd\tau=\Delta V_{dc}^{2}$$

$$\Delta V_{dc}^{2}=\frac{2}{C_{dc}}\cdot\int_{0}^{t}\Delta Pd\tau$$

Where $$\Delta P=(P_{out}(\tau)-P_{pv}(\tau)).$$

The formula:

$$\theta(t)=\omega_{0}t+K\cdot\left(\frac{2}{C_{dc}}\int_{0}^{t}(P_{out}(\tau)-P_{pv}(\tau))d\tau\right)$$

• $\theta(t)$:Instantaneous direct phase angle output of the inverter at time t(rad).

• $\omega_{0}$: The nominal grid angular frequency measured in radians per second ($rad/s$).

• $K_{r}$: A ripple compensation gain, dictating the feedback Sensitivity to DC-link fluctuations ($rad/V^2$)

• $C_{dc}$ Total equivalent capacitance of the DC-link energy storage Stage (F).

• $P_{out}(\tau)$ Instantaneous active power exported to the AC grid at Integration time $\tau(W)$.

• $P_{pv}(\tau)$: Instantaneous harvested photovoltaic power entering the DC-link at integration time $\tau(W)$

• $\tau$: Dummy variable of integration representing historical time Progression.

Numerical Case Studies:

To validate the mathematical symmetry of the proposed formulation, three operational scenarios are evaluated using a 50Hz grid frequency $(\omega_{0}=314.159~rad/s)$, at time $t=0.01$ s (making $\omega_{0}t=3.1416~rad).$ with $C_{dc}=1.0~F$, and $K_{r}=0.01~rad/V^2$. The definite integral is simplified over a $\Delta t=0.01s$ step as $\int\Delta P(\tau)d\tau\approx\Delta P\times0.01$

Case 1: Steady-State Balance ($P_{out}=1000~W$, , $P_{pv}=1000$) :

$$\Delta P=1000-1000=0W\rightarrow\int_{0}^{0.01}0W=0]$$
$$\theta(t)=(3.1416)+0.01\times\left(\frac{2}{1.0}\times0\right)=3.1416~\text{rad}$$

$$\theta(t)=\omega_{0}t$$

Case 2: Transient Power Deficit ($P_{out}=1500~W$ $P_{pv}=1000$)

$$\Delta P=1500-1000=+500W\rightarrow\int_{0}^{0.01}+500W=+5]$$
$$\theta(t)=(3.1416)+0.01\times\left(\frac{2}{1.0}\times5\right)=3.2416~\text{rad}$$

$$\theta(t)>\omega_{0}t$$

Case 3: Transient Power Surplus ($P_{out}=1000W$, $P_{pv}=1500$):

$$\Delta P=1000-1500=-500W\rightarrow\int_{0}^{0.01}-500W=-5]$$
$$\theta(t)=(3.1416)+0.01\times\left(\frac{2}{1.0}\times(-5)\right)=3.0416~rad$$
$$\theta(t)<\omega_{0}t$$

The following table:

| Operational State | $P_{out}(W)$ | $P_{pv}(W)$ | Net Energy (J) | Correction $\Delta\theta$ (rad) | Final Angle $\theta(t)$ (rad) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Steady-State | 1000 | 1000 | 0 | 0 | 3.1416 |
| Power Deficit | 1500 | 1000 | +5 | +0.1 | 3.2416 |
| Power Surplus | 1000 | 1500 | -5 | -0.1 | 3.0416 |

Appendix:

$$\omega_{0}t=\frac{rad}{s}\cdot s=rad$$

$$\int(P_{out}(\tau)-P_{pv}(\tau))d\tau=W\cdot s=\frac{J}{s}\cdot s=J$$

$$\left[\frac{\int(P_{out}(\tau)-P_{pv}(\tau))d\tau}{C_{dc}}\right]=\frac{J}{F}=\frac{1}{\left(\frac{1}{V^{2}}\right)}=V^{2}$$

$$K\cdot\left[\frac{...}{C_{dc}}\right]=\frac{rad}{V^{2}}\cdot V^{2}=rad$$

$$\theta(t)=rad+rad=rad$$
