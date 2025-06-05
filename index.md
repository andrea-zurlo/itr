<script src="https://tikzjax.com/v1/tikzjax.js"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script> <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


# Notes – Introduction to Research (a.y. 24-25)

## June 05

### Experimental setup
The measurements are done with a "Flash DSC" (Mettler Toledo) machine that features a microscopy and a chip holder. Once the holder is closed, the machine and the chip form a DSC instrument inside an isolated chamber (?). Each chip features two 80 µm diameter disc made of (aluminum/gold) that consitute the crucibles of the typical macroscopic calorimeter. The use of such small samples allows to work with much higher heating/cooling rates since a small mass has an higher specific heat capacity. Each disc of the chip is equipped with a pair of thermocouples and two disspative resistors. All these components are mounted on a white plastic tile with a side of 2÷3 centimeters and soldered to gold pins ready to be mounted on the machine. Each chip-tile is numbered and has its own calibration. The samples are 40÷50 µm size specimen of GaSe. The GaSe specimen are prepared in the physics laboratory starting from pure powders. The chamber is conneected to a pump that keep the system at constant pressure and that can provide a thermal gas (e.g. nitrogen). This gas is used to dissipate heat from the chip (needed for cooling) and eventually can be a *chiller*, i.e. a gas that allows to reach temperatures below 0 ºC.

### Differential Scanning Calorimetry (DSC)
The working principle of the DSC is the simultaneous measure of the heat flux of two identical crucibles, one empty called reference and one containing the sample. The net heat flux of the specimen during a certain thermal treatment can be estimated by the difference between the one of the sample and the one of the reference

$$ \Phi = \dot{Q}_s - \dot{Q}_r $$

In facts the contribution of the sample is due both to the sample alone and the crucible containing the sample.

In particular we can establish a blance between the two heat fluxes as a sum of multiple contributions: the heat stored/released by the microscopic degrees of freedom of the sample (specific heat) and the heat exchanged with the environment of the chamber.

$$ \dot{Q}_s = m_s c_{ps} \Delta T + m_r c_{pr} \Delta T + \dot{Q}_\text{s,conv} \qquad\qquad \dot{Q}_r = m_r c_{pr} \Delta T + \dot{Q}_\text{r,conv} $$

$$ \dot{Q}_\text{s,conv} = h A_s (T - T_f) \qquad\qquad \dot{Q}_\text{r,conv} = h A_r (T - T_f) $$

Usually we expect [] but here the two contact surfaces with the convective gas are very different $A_r\ll A_s$. This unavoidable difference result in a permanent baseline in the heat flux vs. tempeature curve. 

The heating/cooling of the system is done via the dissipative resistors. The machine is able to measure and control the heat provided to the system in order to follow a predetermined thermal profile (method), i.e. temperature vs. time. The result is a measure of the rate of heat flow (mJ/s or mW) vs. temperature (ºC or K).

The typical heating curve shows an almost linear trend in the first phase until the glass transition is reached. Here it undergoes a positive peak that is associated to the release of energy (exoergonic). Then it keeps to increase linearly but with a different slope. From such a slope the dependence of the specific heat with respect to the temperature can be inferred (see Debye and Einstein models, degrees of freedom, etc.). The higher the heating rate the lower the peak height because the glass is able to release more energy during slower thermal processes.






