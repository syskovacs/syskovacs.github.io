---
layout: post
title: Big data kezelés - 3.rész
---

A rendszer kiépítéséhez két virtuális gép állt rendelkezésre KVM alapon virtualizálva. Sajnos a két gép hardveres kiépítése alulmúlta a felhasználásra kerülő Cloudera CDH megoldásának igényeit, így több helyen egyedi konfigurációt kellett alkalmazni.

A Cloudera disztribúciójának nagy előnye, hogy fejlett grafikus felülettel rendelkezik, ami megkönnyíti a menedzsment feladatok elvégzését, a linux rendszerekben kevésbé jártas felhasználók számára is információt szolgáltat. A beállításban segítségemre voltak a már említett Tuning Spreadsheet-ek.

![image](http://i.imgur.com/dpor7Dy.png "Rendszer részletek")

A kiépítés első lépéseként a gépeink közötti SSH hozzáféréseket kellett kialakítani, majd a CDH telepítő segítségével megkezdeni a rendszer felépítését. A telepítés után kezdődött meg a Docker klaszter kiépítése a fent nevezett két gépen, amely a Rancher használatával jött létre. Ez a későbbiekben hasznos segédeszköz lehet, grafikus felülete nagyban megkönnyítheti a későbbi menedzsment feladatok elvégzését. A CDH modulok kiválasztása során figyelmet fordítottam a gépek közti elosztásukra, a célszerűség elvét követve némelyek mindkét gépre, mások csak az egyik gépre kerültek beállításra. A Flume, Hive, Hue és Impala kiegészítő modulok kerültek beállításra a szerveren, mindegyik az alapértelmezett portján kommunikál.

Ahogy a hardverspecifikációból látható, ez csupán egy modell, production környezetben nem állná meg a helyét, főként a szegényesen rendelkezésre álló tárterület miatt. Mindezek ellenére a létrehozása során számos tapasztalattal gazgadodtam, amiket a későbbiekben reményeim szerint haszonnal kamatoztathatok.
