# UREI-1603-PSU-Upgrade-Switch-Mode-Rebuild-Tutorial
Instructions to replace the original PSU for a reliable switching-PSU to prevent damages from over-voltages


The UREI 1603 is an amazing fully analog DJ/club mixer.

Its original power supply is known to fail after several thousand operating hours, producing over-current and unstable DC rails that will damage the mixer over time. 

Commercial workshops offer PSU replacements for high prices, often several hundred pesos for a conceptually simple solution using standard power modules.

In this Tutorial, you will replace your 1603 PSU for about 20 bucks.

The ±12 V rails provide sufficient operating range for all audio and control ICs in the mixer.

The original ±16 V and +8 V rails are not mandatory for proper function, and their replacement does not reduce reliability or safety.

Operating the analog path at ±12 V stays within the acceptable limits of the original circuit design and is a technically reliable and electrically safe solution for long-term use.


This guide is published to provide transparent, reproducible Open-Source knowledge, enabling users to understand the rebuild and perform it independently.

**Replace the original PSU section with:**
* Two isolated 12V DC switch-mode PSU modules to form ±12V rails for the analog audio path
* One 7809 linear regulator stage to generate a clean +9V rail as a stable replacement for the internal +8V logic rail
* Bypass all original ±16V linear regulation stages to eliminate heat and stress

**Required Components**

2× 12V DC SMPS units	Isolated, stable, low-noise, 1.5–2A each, adjustable via trim-pot (Meanwell RS-15-12)

1× 7809 Linear Regulator	TO-220 type, 9V output, 1A max (e.g., MC7809CTG or LM7809 equivalent)

DC wiring	0.5–1 mm² copper, insulated

Insulation & mechanical	Shrink tubing and secure mounting for PSUs

**PSU Rebuild Wiring**
1. Mains Input
230 VAC IN → Both 12V PSUs


**2. Forming the ±12V Audio Rails**

Cut all wires to/from the old PSU and remove that sucker.

![IMG_0255 2](https://github.com/user-attachments/assets/fccbd49f-568b-48f0-bd84-b82d81dbb92a)

* You start from the red wire (8V+):
* The red wire remains loose, 8V coming later from the Regulator
* GND to PSU1 negative
* +16V to PSU1 positive
* GND + GND to PSU2 positive (common ground reference)
* –16V to PSU2 negative

**Result on the mixer PCB witch new PSU:**

The Master-PCB now distributes ±12V internally as a replacement for the former ±16V rails.

![IMG_0268](https://github.com/user-attachments/assets/ff632b91-5631-466a-b691-02598dfb3b4a)


![IMG_0252 2](https://github.com/user-attachments/assets/e34f9d1f-ff22-41f6-acbc-1e3009adcbe5)

**3. Generating the +9V Logic Rail (7809 Stage)**

7809 Pin	Connection

1 (IN)	PCB pad labeled "+16V"

2 (GND)	PCB Ground (mixer internal GND pad)

3 (OUT)	PCB pad labeled "+8V"

This feeds +9.0V regulated into the logic section that was originally labeled +8V.

![IMG_0243 2](https://github.com/user-attachments/assets/91bf8613-4571-4749-8347-fb8e685c3f9c)

**Voltage Trimming**

* Trim both PSUs to 12.0–12.2 V

* 7809 output is fixed at 9.0 V

* Typical mixer load is ~200–400 mA, so 1 A capability is sufficient

**Post-Upgrade Verification**

Measure on the Master-PCB:

PCB Pad	Target	Tolerance

+8V	+9.0V DC	±5 %

+16V	+12.1V DC	±10 %

–16V	–12.1V DC	±10 %

If values are within range, the PSU rebuild is electrically correct.

**Final Result**

* Mixer remains 100% analog

* Runs cooler and more stable

* PSU stress and destructive over-current issue removed

* No digital audio or DSP rails introduced

* Audio circuitry (Op-Amps/VCA) tolerates ±12V operation safely

* Output headroom is slightly reduced vs. ±16V but remains fully functional and stable

Disclaimer

You perform all modifications at your own risk. Always insulate all wiring properly, avoid accidental DC shorts, and confirm correct polarity before first power-on.


Permission is granted to use, modify, and share this documentation freely.
