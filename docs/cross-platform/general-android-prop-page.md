---
title: Ogólne właściwości projektu (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4526a329b4e047a449995b7b5ef66362aff1cc8f
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950583"
---
# <a name="general-project-properties-android-c"></a>Ogólne właściwości projektu (Android C++)

Właściwość | Opis | Decyzji
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez ten projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez ten projekt. (Przykład: *. exe* lub *. dll*)
Rozszerzenia do usunięcia podczas czyszczenia | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, dla których pliki w katalogu pośrednim mają zostać usunięte podczas czyszczenia lub odbudowy.
Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone.
Zestaw narzędzi platformy | Określa zestaw narzędzi używany do tworzenia bieżącej konfiguracji; Jeśli nie zostanie ustawiona, używany jest domyślny zestaw narzędzi
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)** — Biblioteka dynamiczna ( *. tak*)<br>**Biblioteka statyczna (. a)** — Biblioteka statyczna ( *. a*)<br>**Narzędzia — narzędzie**<br>**Reguł programu make** — plik reguł programu make<br>
Docelowy poziom interfejsu API | Poziom interfejsu API NDK dla systemu Android, którego dotyczy ta konfiguracja.
Użycie STL | Określa, C++ która Biblioteka standardowa ma być używana dla tej konfiguracji. | **Minimalna C++ Biblioteka środowiska uruchomieniowego (system)**<br>**C++Biblioteka statyczna środowiska uruchomieniowego (Gabi + + _static)**<br>**C++udostępniona biblioteka środowiska uruchomieniowego (Gabi + + _shared)**<br>**Biblioteka statyczna środowiska uruchomieniowego STLport (stlport_static)**<br>**Biblioteka udostępniona środowiska uruchomieniowego STLport (stlport_shared)**<br>**Biblioteka statyczna GNU STL (gnustl_static)**<br>**Udostępniona biblioteka GNU STL (gnustl_shared)**<br>**Biblioteka statyczna LLVM libc + + (c++ _static)**<br>**Biblioteka udostępniona LLVM libc + + (c++ _shared)**<br>
Tryb przewijania | Generuj kod, który jest wykonywany dla mikroarchitektury przycisku przewijania. Dotyczy to tylko architektury ARM. | **Odcisk**<br>**ARM**<br>**Disabled (Wyłączone)**<br>
