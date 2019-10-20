---
title: Zdarzenie przed kompilacją — okno dialogowe wiersza polecenia zdarzenia po kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b42c219620a669a8fa27a7ce847dc571a4075288
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662164"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz wpisać zdarzenia przed lub po kompilacji dla [strony zdarzenia kompilacji, Projektant projektuC#()](../../ide/reference/build-events-page-project-designer-csharp.md) bezpośrednio w polu edycji lub wybrać makra przed i po kompilacji z listy dostępnych makr.

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika
 **Pole edycji wiersza polecenia** Zawiera zdarzenia do uruchomienia na potrzeby wstępnej kompilacji lub po kompilacji.

> [!NOTE]
> Dodaj instrukcję `call` przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Makra** Rozwija pole edycji, aby wyświetlić listę makr do wstawienia w polu edycji wiersza polecenia.

 **Tabela makr** Wyświetla listę dostępnych makr i jego wartość. Aby uzyskać opis każdego z tych elementów, zobacz poniższe makra. Można wybrać tylko jedno makro naraz, aby wstawić je do pola edycji wiersza polecenia.

 **Wstaw** Wstawia do pola edycji wiersza polecenia makro wybrane w tabeli Macro.

### <a name="macros"></a>Makra
 Możesz użyć dowolnego z tych makr, aby określić lokalizacje plików lub uzyskać rzeczywistą nazwę pliku wejściowego w przypadku wielu zaznaczeń. W tych makrach nie jest rozróżniana wielkość liter.

|Makro|Opis|
|-----------|-----------------|
|`$(ConfigurationName)`|Nazwa bieżącej konfiguracji projektu, na przykład "Debugowanie".|
|`$(OutDir)`|Ścieżka do katalogu wyjściowego pliku, względem katalogu projektu. Jest to rozwiązanie do wartości właściwości katalog wyjściowy. Zawiera końcowy ukośnik odwrotny "\\".|
|`$(DevEnvDir)`|Katalog instalacji programu Visual Studio (zdefiniowany przy użyciu dysku i ścieżki); zawiera końcowy ukośnik odwrotny "\\".|
|`$(PlatformName)`|Nazwa aktualnie dostosowanej platformy. Na przykład "AnyCPU".|
|`$(ProjectDir)`|Katalog projektu (zdefiniowany przy użyciu dysku i ścieżki); zawiera końcowy ukośnik odwrotny "\\".|
|`$(ProjectPath)`|Nazwa ścieżki bezwzględnej projektu (zdefiniowana przy użyciu dysku, ścieżki, nazwy podstawowej i rozszerzenia pliku).|
|`$(ProjectName)`|Podstawowa nazwa projektu.|
|`$(ProjectFileName)`|Nazwa pliku projektu (zdefiniowana z nazwą podstawową i rozszerzeniem pliku).|
|`$(ProjectExt)`|Rozszerzenie pliku projektu. Zawiera "." przed rozszerzeniem pliku.|
|`$(SolutionDir)`|Katalog rozwiązania (zdefiniowany przy użyciu dysku i ścieżki); zawiera końcowy ukośnik odwrotny "\\".|
|`$(SolutionPath)`|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowanego przy użyciu dysku, ścieżki, nazwy podstawowej i rozszerzenia pliku).|
|`$(SolutionName)`|Podstawowa nazwa rozwiązania.|
|`$(SolutionFileName)`|Nazwa pliku rozwiązania (zdefiniowana z nazwą podstawową i rozszerzeniem pliku).|
|`$(SolutionExt)`|Rozszerzenie pliku rozwiązania. Zawiera "." przed rozszerzeniem pliku.|
|`$(TargetDir)`|Katalog podstawowego pliku wyjściowego kompilacji (zdefiniowany przy użyciu dysku i ścieżki). Zawiera końcowy ukośnik odwrotny "\\".|
|`$(TargetPath)`|Nazwa ścieżki bezwzględnej podstawowego pliku wyjściowego dla kompilacji (zdefiniowana z dyskiem, ścieżką, nazwą bazową i rozszerzeniem pliku).|
|`$(TargetName)`|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|
|`$(TargetFileName)`|Nazwa pliku podstawowego pliku wyjściowego dla kompilacji (zdefiniowana jako nazwa podstawowa i rozszerzenie pliku).|
|`$(TargetExt)`|Rozszerzenie pliku podstawowego pliku wyjściowego dla kompilacji. Zawiera "." przed rozszerzeniem pliku.|

## <a name="see-also"></a>Zobacz też
 [Określanie niestandardowych zdarzeń kompilacji na](../../ide/specifying-custom-build-events-in-visual-studio.md) [stronie zdarzeń kompilacji programu Visual Studio, Projektant projektuC#()](../../ide/reference/build-events-page-project-designer-csharp.md) [instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
