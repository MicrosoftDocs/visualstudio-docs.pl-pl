---
title: Właściwości debugera systemu android (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 9a4d7baa970008c2de7a3bc28966f7edbad68b21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62819506"
---
# <a name="android-debugger-properties"></a>Właściwości debugera systemu android

Właściwość | Opis | Opcje
--- | ---| ---
Typ debugera | Określa typ kodu do debugowania. | **Tylko w trybie macierzystym**<br>**Tylko dla środowiska Java**<br>
Docelowy debugowania | Określa emulator lub urządzenie używane do debugowania. Jeśli nie uruchomiono żadnych emulatorów, następnie użyj "Android Virtual Device (AVD) Manager" do uruchomienia urządzenia.
Pakiet do uruchomienia | Określa lokalizację *.apk* który będzie debugowany. Wybierz tę opcję, aby określić, że określony pakiet (APK) powinna być uruchamiana podczas debugowania aplikacji.
Działanie uruchamiania | Działanie systemu Android używane do uruchamiania aplikacji, ma być zgodne z działaniem używanym w manifeście. Naciśnij przycisk Zastosuj, aby pobrać listę z *AndroidManifest.xml* i wypełnić ją dynamicznie.
Dodatkowa ścieżka wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania symboli debugowania.
Ścieżki wyszukiwania źródła Java dodatkowe | Dodatkowe ścieżki wyszukiwania dla plików źródłowych Java. (Dotyczy tylko kiedy typ debugera jest tylko Java).
