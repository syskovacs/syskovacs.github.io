---
layout: post
title: Big data kezelés - 4.rész
---

A Cassandra egy sémamentes adatbázis megoldás, ami alkalmas arra, hogy nagy mennyiségű adatot tároljunk le benne vagy kérdezzünk le belőle. Ezt az adatbázis megoldást Docker konténerek használatával telepítettem a szerverekre, azokból egy két gépes klasztert létrehozva. A Docker és a Linux közösen használja a kernelt. A szükséges izolációkat Linux namespace-k, cgroups és UnionFS fájlrendszer felhasználásával biztosítja. A Linux rendszerek 6 különböző névteret különböztetnek meg. Ennek a legnagyobb jelentősége az, hogy folyamatok egy csoportjának egy olyan környezetet tudnak biztosítani, amelyben ők az egyedüli folyamatok. A Docker alapvetően két fő, jól elkülönülő részből áll. A Docker Engine a helyi gépen, szerveren fut, feladata a konténerek kezelése, futtatása. A Docker Hub egy felhő alapú szolgáltatás, ami képfájlok beszerzését, publikálását teszi lehetővé. A beállítások elvégzéséhez így a Docker Engine csomagjait is konfigurálni kellett mindkét gépen, majd beszerezve a nevezett Cassandra képfájlt mindkét gépen beállítani a konténereket belőle, olyan módon, hogy azok elérhessék egymást. A beállítások sikerességét az alábbi kimeneten ellenőriztem.

_root@kovacsd:~$ docker exec -it 226b7b96dd1e nodetool status
Status=Up/Down/ State=Normal/Leaving/Joining/Moving
--  Address        Load       Tokens  Owns    Host ID                               Rack
UN  172.20.16.133  61.64 MB   256     ?       13641199-6fc6-4940-8b31-c041729b3619  rack1
UN  172.20.16.134  61.52 MB   256     ?       6e956ca3-68c7-4d0c-99d2-c4dad9953562  rack1_
