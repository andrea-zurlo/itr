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

Usually we expect $\dot{Q} \approx \dot{Q}$ but here the two contact surfaces with the convective gas are very different $A_r\ll A_s$. This unavoidable difference result in a permanent baseline in the heat flux vs. tempeature curve. 

The heating/cooling of the system is done via the dissipative resistors. The machine is able to measure and control the heat provided to the system in order to follow a predetermined thermal profile (method), i.e. temperature vs. time. The result is a measure of the rate of heat flow (mJ/s or mW) vs. temperature (ºC or K).

The typical heating curve shows an almost linear trend in the first phase until the glass transition is reached. Here it undergoes a positive peak that is associated to the release of energy (exoergonic). Then it keeps to increase linearly but with a different slope. From such a slope the dependence of the specific heat with respect to the temperature can be inferred (see Debye and Einstein models, degrees of freedom, etc.). The higher the heating rate the lower the peak height because the glass is able to release more energy during slower thermal processes.


## June 25

### Experimental set up
Differently from what has been told me the last time, I will work with boron oxide (B2O3) samples. The preparation of experimental set up is made of the following steps:
1. chip selection and mounting – the chip must be chosen from the set of available chips and mounted on the instrument. When this is done it is important to note down the chip serial number.
2. preparation of the specimen – To clean the slide with acetone and ethylene. Boron specimen are higly hygroscopic, for this reason are kept inside closed containers with silica. At first, the sample has the form of a small piece of milky glass. The opacity is due to the presence of water. The sample is mechanically broken in little pieces (powdered at human sight) on the slide by means of laboratory tools, like tweezer and lancet. The slide is then positioned on the aperture above the sample holder of the calorimeter. With the help of a bristle the chip is cleaned and the specimen is positioned.
3. Nitrogen inlet – between 20 and 30.
4. conditioning and calibration – these processes must be conducted before the measurements are started.
5. method drawing

### File format
The instrument outputs data files in `.txt` format. The measurements have the following naming convention 
```
[sample]_[method]_[chip]_[incremental]
``` 
Each file contains a table of raw numeric data acquired by the instrument. This features the timestamp `t [s]`, the sample temperature `Ts [ºC]`, the reference temperature `Tr [ºC]` and the power supplied to the system at that specific time `Value [mW]`. A data file contains several headers: one for each method segment and eventually one for each repetition of the same measurement, determined by the incremental number.

```
Title                                                           28.04.2023 17:25
________________________________________________________________________________

Title


Curve Name:
  ]15[&Pd_22_360_H=C500_X5_72886_002
Curve Values:
          Index              t             Ts             Tr          Value
                           [s]           [�           [�           [mW]
              0              0        359.203        360.000        0.50914
              1         0.0001        359.253        359.950       0.508844
              2         0.0002        359.300        359.900       0.509139
              3         0.0003        359.345        359.850       0.510426
              4         0.0004        359.384        359.800       0.512094
              5         0.0005        359.415        359.750       0.513141
              6         0.0006        359.437        359.700       0.513012
```

### Baseline symmetric correction
Usually the thermograms feature a linear increase overlapped to the glass transition. This is due to a spurious heat flux contribution $HF_0$ related to contact betwen the sample and the gaseous nitrogen present in the calorimeter cell. This contribution is supposed to be equal for both the heating and the cooling process
$$ HF = m c_p q_h + HF_0 $$
$$ HF = -m c_p q_c + HF_0 $$
To remove this background baseline we employ the symmetric correction. It is called symmetric because we require the heating and the cooling rates to be equal $|q_h| = |q_c|$. To obtain the baseline we exclude from the data the nose and the tail of the curves and the portion relative to the enthalpy recovery peak. Then with this data we calculate the average of the heating and the cooling curve and we fit the result with a polynomial. Finally we subtract the baseline from the initial data.


## June 26
### Enthalpy relaxation
To obtain the thermogram of a specimen, we apply two groups of thermal cycles (referred to as methods). The first group consists of a fast heating ramp followed by a cooling curve—this is called the preparation step. The second group involves both heating and cooling ramps at the same fast rate and is referred to as the probing step. The rate used during the preparation step, also known as the *quenching* rate, determines the vitreous character of the specimen.

At low quenching rates, the resulting thermogram typically shows a single positive overshoot peak along the liquid line, referred to as the *alpha peak*. As the rate increases, a second, negative peak—the *beta peak*—emerges along the solid line. To identify and characterize the beta peak, we perform a series of measurements as a function of the quenching rate. Since the relaxation process exhibits exponential behavior, we use a logarithmic scale of quenching rates (e.g., 1, 10, 100, 1000, 10000 K/s), which allows us to clearly observe the emergence of the beta peak and to identify an appropriate relaxation temperature for further study. Typically, this temperature is chosen below the range where the solid-line peak appears, though other positions may be considered depending on the application.

Next, we investigate how the enthalpy associated with the beta peak changes with relaxation time at a fixed temperature. We select four or five temperatures within the previously determined range. The enthalpy is obtained by integrating the area under the beta peak. By varying the relaxation temperature, we aim to identify conditions where the alpha peak remains constant while the beta peak varies.

When we plot enthalpy versus relaxation time, we expect to observe a decreasing curve similar in shape to the cumulative distribution function (CDF) of a normal distribution. The width of this curve depends on the relaxation temperature and reflects an underlying activation process. We associate this width with a characteristic time constant, $\tau$, which we estimate by fitting the enthalpy-time curve at each relaxation temperature.

Finally, we plot $\log{\tau}$ versus $1/T$. The slope of the resulting linear trend provides information about the activation energy, $\Delta E$, using the Arrhenius-type relationship:
$$ \tau = \tau_0 e^{\Delta E/ k_B T} $$ 
where $\tau_0$ is a pre-exponential factor and $k_B$ is the Boltzmann constant.

### Quenching rate measurements #1
We used B$_3$O$_2$ samples with chip no. 72866 and performed measurements across a range of cooling rates within the temperature interval 25–460 °C. For cooling rates exceeding 800 K/s, we observed an unexplained oscillating noise in the lower-temperature region of the cooling curve, specifically during the quenching segment. This noise may be attributed to the relatively large mass of the particular specimen used in these tests.


## June 27
### Electronic noise
We have advanced some hypthesis about the noise found in the measurements done yesterday, with the chip no. 72866. Firstly, we thought to the large mass of the specimen or the fact the the spacimen was overlapped to the thermocouples but later we convinced ourselves it was related to the noise in the electronics. The fact that it araises at larger cooling rates was not explained. 

We decided to discard the measurements and start from the beginning with a new chip.

### Quenching rate measurements #2
We choose a new chip (no. 72804) and we perform 3 calibration runs to it. We clean the slide and prepare the B$_3$O$_2$ specimen. This time we had no problems with the polarization of the bristle and the slide and we have found a piece that has the right size to fit the sample holder.

First we applied an isotherm at 200 ºC followed by two heating-cooling cycles, and we repeated this few times. This is done to nurture the dissociation of the boric acids in the samples and to get as close as possible to a pure boria compound.

After that we performed the measurements at various quenching rataes.

### Secondary chip calibration
This is done by exploiting the melting temperature of well known materials. In particular, at low temperatures we can use boric acid (200 ºC) or benzoic acid (122 ºC). At higher temperature are used metals ir crystals in general. The problem with the crystals is that they cannot be removed from the sample holder so this must be done at the end of the measurement. Usually this secondary calibration is done in the lower active area of the chip, the one related to the reference.

Here the chip no. 72866 has been used and it has been found that the regular chip calibration done by the instrument was quite good. To correctly perform the calibration the onset of the melting must be determined using the derivative of the curve at the beginning of the endo peak.