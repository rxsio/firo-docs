---
title: Radiation Protection
---

!!! outdated
    This section need update

## Radiation effects on electronics
Apparently radiation is able to generate charges inside semiconductors and destroy thin insulators like silicon oxide commonly used in semiconductor components. This sort of behavior can lead to memory corruption which can interrupt any sequential electronic device. The damage can be temporary if only one or few bits get changed. Also there is a risk of latch-up in logic circuitry. Damage can also be permanent.

!!! outdated
    This section needs to be refined. Include:
    - what components are fragile to radiation
    - at what levels they are fragile
    - what is effect of the radiation on this component

## Possible solutions
Luckily there are ways to manufacture more radiation resistant devices. Most of them require use of different semiconductor technology:
* Gallium arsenide instead of silicon,
* SOI instead bulk technology (unlikely to latch because of better insulation of every transistor),
* BJT instead of FET (does not have thin insulators at all),
* SRAM instead of DRAM (DRAM is based on charge storing).
Making bigger transistors with thicker gate insulators also helps. There are radiation hardened integrated circuits on the market. There is also to mount protective shields outside circuit boards.

!!! outdated
    This section needs to be refined
    - include new and fixed possible solution
    - describe at what radiation levels the solution seems feasible

## Our preffered solution
Unfortunately radiation hardened integrated circuits and even discreet components are both hard to access and very expensive (more than 50€ for quadruple logic gate). On this field we can only choose components based on technology there were manufactured and assume which one will be more durable.

There is possible to use shields which can stop part of the radiation. The most cost-efficient idea is to implement software solution. Rover would operate more reliably if it could detect errors in its memory and correct them using correction algorithm or downloading data from external, more distant from source of radiation, drive. This memory does not have to be very distant. It is possible to use different kind of affordable storage like magnetic hard disc drive or optical compact disc.

!!! outdated
    This section needs to be refined
    - shielding works best for alpha and beta radiation - for gamma radiation shielding is not enough (eg. requires 2.8cm of lead to reduce radiation by ~x100)
    - describe more error detection and correction - describe ECC memory (only hardware solutions are fast enough for RAM memory), describe better filesystems (they can correct corrupted blocks)
    - add reasons why optical compact discs and hard disc drives are better than solid-state drives 


!!! outdated
    New section required

    Cover all issues that can affect rover
    - describe the cause (eg. gamma radiation)
    - describe the component (eg. BIOS)
    - describe issue (eg. bit flip in boot code)
    - estimate severity of issue (eg. critical)
    - describe countermeasures