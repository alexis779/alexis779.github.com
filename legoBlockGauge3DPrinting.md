# Gauge

The goal is to assess the 3D printer calibration. First 3D-print a gauge to make sure the future 3D-printed parts will have a tight fit.

This video describes checking the gauge on a [servo](https://www.alibaba.com/product-detail/STS3215-SERVO-FOR-AI-Autonomous-Racing_1601053797763.html?spm=a2756.order-detail-ta-bn-b.0.0.4eecf19cj1NY97) piece. To assemble both the leader and follower arms, order 12 units.

[![Servo gauge](https://img.youtube.com/vi/dss8E3DG2rA/0.jpg)](https://www.youtube.com/watch?v=dss8E3DG2rA)

While waiting for the servo order, you can still start on the [4x2 lego block gauge](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Gauges/Lego_Size_Test_02_zero.STL)


## 3D Printer

The 3D printer is a [Lulzbot TAZ 6](https://lulzbot.com/store/taz-6).

![Lulzbot TAZ 6](https://lh3.googleusercontent.com/pw/AP1GczMq_0_XTV68B2jD0Bpofgy4X-_rxDsLilXcekwF668-CRcqoozZWqxQUqBTyWR9yso6At-8SIU4IHVsc1EDjUZoKaWvozo8FJJPNluxIryXIXCmSqgLCYD_qH0Jcb7uz3PBBxWBu0JSJc_e3RoeZYubtA=w961-h961-s-no-gm?authuser=0)

The filament material is PLA.

![PolyTerra PLA](https://lh3.googleusercontent.com/pw/AP1GczPeqyadM2vlkJUtfjALBzf-QMLDCRp8unLnJjNwtNJv7IUsTI4fr5VuzbJTxCsrYrjUt1pAzHKfrPS-GnhtyntDiyI_yZnH54Nheg-p0MYQ61IFe0NxA3P8Eu7CIvozMmGhQ2LgyZc_9-EUPzcU9Q9Rgg=w961-h961-s-no-gm?authuser=0)


### Failures

The 1st attempt to print the part fails due to *bed adhesion* issue after printing a few layers.

Adding a *skirt* or a *brim* does not help.

![Bed adhesion failure](https://lh3.googleusercontent.com/pw/AP1GczOvn6O3VyZkbSh3VTXbLHb618gQFO0ZMJspCweSUjkc-us5F2wf79Zope_57UI4GCR9yZ7p_LEhPTtl-tBCu49FKvMcl2RWr47izrn8ajIkaANbd9M2T9FWFOdiFhXbRi04uPgdS92F5D8aAzRZ9eCbEg=w1708-h961-s-no-gm?authuser=0)

Looking at the slicer, we notice after the 2 bottom full layers, the hollow layers contain those zigzags across the interior between the inner walls. This may have caused some transversal forces on the wall, creating a rotating moment on the piece.

![Cura slicer](https://lh3.googleusercontent.com/pw/AP1GczOIjzQzoChMCtPAs6z_ReboDBHsa5GhjynT6B5pDU-uiOjPipyCDzN_d5P6VUsFcD1dbWDvzr6XaOoRaSl0QLVUlX-fmLmXpzGLXPI9dOQuxunLmp_kz09sTUFyGDlE-PR4IAlAZrnS1ac-gHakJ9LkPg=w1761-h961-s-no-gm?authuser=0)


> Due to the infill, the part starts vibrating and finally loses adherence to the heated glass bed.

After setting infill to 0% (no infill), the printer finishes the part successfully, but shows some *warping* on the fist 2-3 layers.

![Warping with no infill](https://lh3.googleusercontent.com/pw/AP1GczO4MOvZ4o_BIcjWcXGBBw67KF8wdFnfA_rwjBOvTB0ZxJ2L2WiTaaLfJZIGJen5sohAK3LuOz1d8pTjTb7vtOx7UE2D7DpItsWfVFeGf9vXDTo1cBbgYqD22j8wqIoC18K7auKYCLXK9Pd732rdyQ77Iw=w541-h961-s-no-gm?authuser=0)


The top face is smooth but the bottom has gaps in the infill area.

| ![Top face](https://lh3.googleusercontent.com/pw/AP1GczN1sqVJXbtpdbikdz_zYLU-yOM6EDFTJj3-vWFV9u3OeCFaTZhb_DvYtuxOmshkLtcZQXhu_Q1Y7nJMckugncVc7-zsH8ULiWcpfqhFbVjGO8CfzTvcnQwxa2lJx7toj0Np2wg7PXC2dP1xLETRVDw4qw=w961-h961-s-no-gm?authuser=0) | ![Bottom face](https://lh3.googleusercontent.com/pw/AP1GczOLPOtPMjc7osDM0joNtU5o0x5OtFX2UUkW0EV0FSev0M-LAoc2atcj7FLt7h3VBrYGfuKY6QmJFPAEqjiyYS5S3FT9pYwhqnuz5Sv3lrOlrCSDCoDSi4MHqsm5dZj2M3NaJdr9MF5kWzjoFzN7pFwTdw=w961-h961-s-no-gm?authuser=0) |
|-|-|
| Top face | Bottom face |

Here are the basic settings

![Basic settings](https://lh3.googleusercontent.com/pw/AP1GczNctTcXVjp0eRPYCyp3_0l-KHyG9eVoSWlcvHTl7-Irn0EbHz5_fFiIDkzcUFUpKZoyxuSkkpkGYcP35M0Qm9wYMx1ORQl0cSFkNxd1gg-YaWI2UUCJuE_l7xpVRM0CE8SVeUSpR8XIyKgNKUhGutrhrQ=w961-h961-s-no-gm?authuser=0)