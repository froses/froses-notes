---
title: Quartz - Flux de treball
draft: false
tags:
  - quartz
  - workflow
---
# Quartz – Flux de treball

Un cop instal·lat i configurat el lloc Quartz en local i sincronitzat amb GitHub, podem començar a crear contingut. 

Tot el contingut s’ha de crear sota la carpeta `content`. Tot el que hi hagi fora d’aquesta carpeta, no es publicarà ni en local ni a GitHub.

Partint, doncs, d’aquesta situació:

## 1. Desplegarem el contingut del nostre celler en local 
Per fer-ho:
1. Ens situarem a la carpeta del celler: `cd ~/notes-`
2. Executarem **`npx quartz build --serve`** per:
	1. Generar l’HTML corresponent al contingut del celler i a la configuració de Quartz.
	2. Arrencar un servidor web local: http://localhost:8080 que:
		1. Ens mostrarà el contingut i 
		2. vigilarà els canvis al celler per actualitzar-los al web local.

## 2. Modifiquem el contingut del celler 

Modifiquem notes, creem noves notes i carpetes, esborrem notes o carpetes… Els canvis són seguits per Quartz que els actualitza al web local.

>[!warning] Avís: 
>Sembla que sincronitza els canvis fets a fitxers existents, però si hem afegit fitxers nous, aquests no se sincronitzen localment de manera automàtica. Cal aturar el servidor local (⌃ + C) i tornar-lo a arrencar perquè agafi els nous fitxers (`npx quartz build --serve`). 

## 3. Sincronitzem amb GitHub 

Quan estiguem satisfets de com ha quedat el nostre contingut (ho hem comprovat amb el servidor local), sincronitzem amb GitHub: **`npx quartz sync`** . 

I ja podrem veure els canvis des d’Internet: [froses-notes](https://froses.github.io/froses-notes/)

