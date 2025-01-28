# Solving the Elephant foot problem on Lulzbot TAZ 6

## 3D Printer

The 3D printer is a [Lulzbot TAZ 6](https://lulzbot.com/store/taz-6), running [Marlin firmware](https://marlinfw.org/).

![Lulzbot TAZ 6](https://lh3.googleusercontent.com/pw/AP1GczMq_0_XTV68B2jD0Bpofgy4X-_rxDsLilXcekwF668-CRcqoozZWqxQUqBTyWR9yso6At-8SIU4IHVsc1EDjUZoKaWvozo8FJJPNluxIryXIXCmSqgLCYD_qH0Jcb7uz3PBBxWBu0JSJc_e3RoeZYubtA=w961-h961-s-no-gm?authuser=0)

## Filament
The filament material is PLA.

![PolyTerra PLA](https://lh3.googleusercontent.com/pw/AP1GczPeqyadM2vlkJUtfjALBzf-QMLDCRp8unLnJjNwtNJv7IUsTI4fr5VuzbJTxCsrYrjUt1pAzHKfrPS-GnhtyntDiyI_yZnH54Nheg-p0MYQ61IFe0NxA3P8Eu7CIvozMmGhQ2LgyZc_9-EUPzcU9Q9Rgg=w961-h961-s-no-gm?authuser=0)

Here are the manufacturer specifications 

| Parameter | Value |
|:---|:---|
| Diameter | 2.85 mm |
| Printing Speed | [30 - 70] mm/s |
| Printing Temperature | [190 - 230] °C |
| Bed Temperature | [25 - 60] °C |
| Fan | ON |


## Issues

### Bed Adhesion issue

The 1st attempt to print the [4x2 lego block gauge](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Gauges/Lego_Size_Test_02_zero.STL)
 fails due to *bed adhesion* issue after printing a few layers.

Adding a *skirt* or a *brim* does not help.

![Bed adhesion failure](https://lh3.googleusercontent.com/pw/AP1GczOvn6O3VyZkbSh3VTXbLHb618gQFO0ZMJspCweSUjkc-us5F2wf79Zope_57UI4GCR9yZ7p_LEhPTtl-tBCu49FKvMcl2RWr47izrn8ajIkaANbd9M2T9FWFOdiFhXbRi04uPgdS92F5D8aAzRZ9eCbEg=w1708-h961-s-no-gm?authuser=0)

Looking at the slicer, we notice after the 2 bottom full layers, the hollow layers contain yellow infill zigzags across the interior between the inner walls.

This may have caused some transversal forces on the wall, creating a rotating moment on the piece. If the part is not well anchored on the bed, it will pop out of its original position, failing the print.

![Cura slicer](https://lh3.googleusercontent.com/pw/AP1GczOIjzQzoChMCtPAs6z_ReboDBHsa5GhjynT6B5pDU-uiOjPipyCDzN_d5P6VUsFcD1dbWDvzr6XaOoRaSl0QLVUlX-fmLmXpzGLXPI9dOQuxunLmp_kz09sTUFyGDlE-PR4IAlAZrnS1ac-gHakJ9LkPg=w1761-h961-s-no-gm?authuser=0)


### Elephant Foot issue
Let's disable the infill in the intermediate layers. It will only be printed on the bottom 2 and top 2 layers.

The 2nd attempts completes succesfully, but shows *layer separation* on the fist 2-3 layers.

![Layer Separator](https://lh3.googleusercontent.com/pw/AP1GczO4MOvZ4o_BIcjWcXGBBw67KF8wdFnfA_rwjBOvTB0ZxJ2L2WiTaaLfJZIGJen5sohAK3LuOz1d8pTjTb7vtOx7UE2D7DpItsWfVFeGf9vXDTo1cBbgYqD22j8wqIoC18K7auKYCLXK9Pd732rdyQ77Iw=w541-h961-s-no-gm?authuser=0)

Notice some gap where the extruded filament "falls" on the bed while printing the first layer:

[![1st layer printing](https://img.youtube.com/vi/cJ8Imoj26MY/0.jpg)](https://www.youtube.com/watch?v=cJ8Imoj26MY)

Cura provides 3 windows to configure print profile

- Basic Settings
- Advanced Settings
- Expert Setting

![Basic Settings](https://lh3.googleusercontent.com/pw/AP1GczNd7ftKN_ATKXNGX_FEzc6qPsOYyLpbUddfy3AQElH4wjz2XF0RIWWgkPyTjz6II2xSdG_LM7b29nQJH9xMinZMzuKyDAVSsDMPcRueQ0eXh5rmEnbGz0BAsF9VaIIRzruJ0-T23-_NwbvwGV_3vdHoMg=w1708-h961-s-no-gm?authuser=0)

![Advanced settings](https://lh3.googleusercontent.com/pw/AP1GczPSnNDlKEEY-WR95tasXOgnJXZPhx0nf79yd92y1JAU182JhocEqwUjuoP81RWWm85PMY6i3kc_4UONPaAJL1FvPFQY9PRLRS-OA7DYoHdJqr5pyH9J6Ht1ecCTAT95rxVSsS26TJpj3IgVM2Hbqk3QQg=w1708-h961-s-no-gm?authuser=0)


[Lulzbot forum thread](https://forum.lulzbot.com/t/warping-with-lulzbot-taz-6/27206) suggests adjusting z offset to lower the position of the nozzle for the 1st layer.

### Final settings

| Setting | Value |
|:---|:---:|
| Probe Z Offset | -2.0 mm |
| Initial Layer Thickness | 0.39 mm |
| Layer Height | 0.38 mm |
| Printing Temperature | 230 °C |
| Bed Temperature | 60 °C |
| Fill Density | 0% |

## Double calibration

### Diagram

![First Layer Height](https://lh3.googleusercontent.com/pw/AP1GczMbnbMpnBohHD7xzs3RChRpaPqtaGIIsAZ9MJskg5R9_5pzneS5y-L5rzhtNJc11uKfZkZqaJmB8IQDIkhNDCloPYy8GLPy12Ji8hDn8ALyscDH4FtVLBhTfZcBW5GnlozSj0LN97Ehbzi5UxxTKGXeIQ=w769-h308-s-no-gm?authuser=0)


### Automatic Bed Leveling

*Automatic Bed Leveling (ABL)* runs before each print to calibrate the `z = 0` position. This will compensate possibly uneven support across the printing area while the nozzle moves to different (x, y) positions at a given layer.

### Washer

To perform this calibration, ABL hits the nozzle against the 4 [washers](https://lulzbot.com/store/4-pack-bed-leveling-washer-kit-kt-hd0044?ref=KT-HD0044), on the 4 corners of the glass bed. Washer thickness is `~ 1.5 mm`.


![Bed Leveling washer](https://lh3.googleusercontent.com/pw/AP1GczM4BOrGtoG4akQjzGePmoBO6ZMtpQ71nuD3W0xZvHw_kEwv3ttiSG4FA2kYNMLdtzoaMC4lPNZJRlBRgBUbmjO7pJoCGABDGyMseblk0ADv_3grtjHAyv0S_dHCi7Uk074ZhRIYHSA1nUc6KNA2EEPo-A=w1110-h817-s-no-gm?authuser=0)


### Probe Z Offset

*Probe Z Offset* parameter also requires calibration. It needs to be done manually. Gradually lower the nozzle position for the 1st layer, until there is no gap above the 1st layer after the first few layers are printed.


Compare the results on 2 values that only differ by 100 microns.

| ![-2.0 mm](https://lh3.googleusercontent.com/pw/AP1GczMIPs0ZovKdvNR8Kv7mYAWEGBVeqVj1bx2-QxhyMchMxw1UwIBTYhp7yVeBpVicYA0YP25jzOjPm3K8yVtWMcGZzUHMmBTg_r7IHaLSbB_oXU2OU_NBL4VLWdo625w_ZjgKKr5ZWvm2cmCT9pBE-KQVrw=w541-h961-s-no-gm?authuser=0) | ![-1.9 mm](https://lh3.googleusercontent.com/pw/AP1GczP7m7DWSrJ0J1zC6JPw0kHD4rEKFUQnEQ_XBxBa2A9KcqoVEv3LC9lU0mjCqQNoI0YSVm7xIYkwog0_8eOi_cLhhWkNItxlMk_nt1MJXBBHz1YtDV1r6_ISARRy2uf93RSj_L9DVI_EDaql6UNfwG1Dkw=w541-h961-s-no-gm?authuser=0) |
|:-:|:-:|
| **-2 mmm** no gap betwe 1st layers and very smooth surface. | **-1.9 mm** some gap between 1st layers and in the infill |




This configuration setting compensates the washer thickness to adjust the position of nozzle close to the glass bed while printing the first layer. The setting is configurable through the LCD display. This [article](https://lulzbot.com/learn/finding-recording-and-restoring-your-z-axis-offset) provides an overview.


![Probe Z Offset](https://lh3.googleusercontent.com/pw/AP1GczO3QQjq5756pHNtC5eKY8kXUFokHSPIfQN9V_XfQJLTfLPXJwhDFLeRLZOXa9rUE-Yeks21GzDj5V6WmlqkA_1x85TKtGBPRbpDQcYL6KrOCKD4uTCN7w8ZvjxPsvTzXnpBYV1XAq3typ_LPMkAUs5LOA=w1708-h961-s-no-gm?authuser=0)


A well calibrated value for the printer was `-2.0 mm`.

## Conclusion

To solve the elephant foot problem, the nozzle should be positioned sufficiently low so that the 2nd layer *squishes* the first layer down on the bed. Calibrating Probe Z offset setting is key to avoid gap in the 1st layers, ensuring the nozzle position leaves exactly the same amount outlined by the initial layer thickness parameter.

This will also increase the bond between the heated glass bed and the part, reducing the risk of failing the print due to bed adhesion issue.

