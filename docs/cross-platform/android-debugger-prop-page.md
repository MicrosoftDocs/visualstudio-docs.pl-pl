---
title: Właściwości debugera systemu AndroidC++() | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 0a052223fe7acac87acf15c5c5091c774451e4e4
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950634"
---
# <a name="android-debugger-properties"></a>Właściwości debugera systemu Android

Właściwość | Opis | Decyzji
--- | ---| ---
Typ debugera | Określa typ kodu do debugowania. | **Tylko w trybie macierzystym**<br>**Tylko Java**<br>
Element docelowy debugowania | Określa emulator lub urządzenie, które ma być używane na potrzeby debugowania. Jeśli nie są uruchomione żadne emulatory, użyj "Menedżera urządzeń wirtualnych systemu Android (AVD)", aby uruchomić urządzenie.
Pakiet do uruchomienia | Określa lokalizację elementu *. apk* , który będzie debugowany. Wybierz tę opcję, aby określić, że określony pakiet (APK) powinien zostać uruchomiony, gdy aplikacja jest debugowana.
Działanie uruchamiania | Działanie systemu Android służące do uruchamiania aplikacji musi pasować do używanej w manifeście. Naciśnij przycisk Zastosuj, aby pobrać listę z *pliku AndroidManifest. XML* i wypełnić ją dynamicznie.
Dodatkowe ścieżki wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania dla symboli debugowania.
Dodatkowe ścieżki wyszukiwania źródła Java | Dodatkowe ścieżki wyszukiwania dla plików źródłowych Java. (Stosuje się tylko wtedy, gdy typ debugera jest tylko w języku Java).
