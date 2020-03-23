---
title: Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji, okno dialogowe
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38712c25718670ea15324e3daf6fadc138cb08a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567921"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Okno dialogowe wiersza polecenia zdarzenia przed kompilacją/po kompilacji

Zdarzenia przed- lub po kompilacji dla [strony Zdarzenia kompilacji, projektanta projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) bezpośrednio w polu edycji lub można wybrać makra przed i po kompilacji z listy dostępnych makr.

> [!NOTE]
> Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i nie zostanie wyzwolona żadna kompilacja.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika

**Pole edycji wiersza polecenia**

Zawiera zdarzenia do uruchomienia w przedskomisję lub po kompilacji.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki .bat. Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

**Makra**

Rozwija pole edycji, aby wyświetlić listę makr do wstawienia w polu edycji wiersza polecenia.

**Tabela makr**

Wyświetla listę dostępnych makr i ich wartości. Opis każdego z nich można znaleźć w makom poniżej. Można wybrać tylko jedno makro naraz, aby wstawić je do pola edycji wiersza polecenia.

**Wstawić**

Wstawia do pola edycji wiersza polecenia makro zaznaczone w tabeli makr.

### <a name="macros"></a>Makra

Za pomocą dowolnego z tych makr można określić lokalizacje plików lub uzyskać rzeczywistą nazwę pliku wejściowego w przypadku wielu wyborów. W tych makrach nie rozróżnia się wielkość liter.

|Makro|Opis|
|-----------|-----------------|
|`$(ConfigurationName)`|Nazwa bieżącej konfiguracji projektu, na przykład "Debug".|
|`$(OutDir)`|Ścieżka do katalogu plików wyjściowych względem katalogu projektu. Spowoduje to rozpoznanie wartości właściwości Katalog danych wyjściowych. Zawiera spływ ukośnika\\wstecznego ' .|
|`$(DevEnvDir)`|Katalog instalacyjny programu Visual Studio (zdefiniowany za pomocą dysku i ścieżki); obejmuje końcowe ukośnik wsteczny '\\" .|
|`$(PlatformName)`|Nazwa aktualnie docelowej platformy. Na przykład "AnyCPU".|
|`$(ProjectDir)`|Katalog projektu (zdefiniowany za pomocą dysku i ścieżki); obejmuje końcowe ukośnik wsteczny '\\" .|
|`$(ProjectPath)`|Bezwzględna nazwa ścieżki projektu (zdefiniowana za pomocą dysku, ścieżki, nazwy podstawowej i rozszerzenia pliku).|
|`$(ProjectName)`|Podstawowa nazwa projektu.|
|`$(ProjectFileName)`|Nazwa pliku projektu (zdefiniowana z nazwą bazową i rozszerzeniem pliku).|
|`$(ProjectExt)`|Rozszerzenie pliku projektu. Zawiera "." przed rozszerzeniem pliku.|
|`$(SolutionDir)`|Katalog rozwiązania (zdefiniowany za pomocą dysku i ścieżki); obejmuje końcowe ukośnik wsteczny '\\" .|
|`$(SolutionPath)`|Bezwzględna nazwa ścieżki rozwiązania (zdefiniowana za pomocą dysku, ścieżki, nazwy podstawowej i rozszerzenia pliku).|
|`$(SolutionName)`|Podstawowa nazwa rozwiązania.|
|`$(SolutionFileName)`|Nazwa pliku rozwiązania (zdefiniowana za pomocą nazwy podstawowej i rozszerzenia pliku).|
|`$(SolutionExt)`|Rozszerzenie pliku rozwiązania. Zawiera "." przed rozszerzeniem pliku.|
|`$(TargetDir)`|Katalog podstawowego pliku wyjściowego dla kompilacji (zdefiniowany za pomocą dysku i ścieżki). Zawiera spływ ukośnika\\wstecznego ' .|
|`$(TargetPath)`|Bezwzględna nazwa ścieżki podstawowego pliku wyjściowego dla kompilacji (zdefiniowana za pomocą dysku, ścieżki, nazwy podstawowej i rozszerzenia pliku).|
|`$(TargetName)`|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|
|`$(TargetFileName)`|Nazwa pliku wyjściowego podstawowego kompilacji (zdefiniowana jako nazwa podstawowa i rozszerzenie pliku).|
|`$(TargetExt)`|Rozszerzenie pliku wyjściowego podstawowego dla kompilacji. Zawiera "." przed rozszerzeniem pliku.|

## <a name="see-also"></a>Zobacz też

- [Określanie niestandardowych zdarzeń kompilacji w programie Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Strona Zdarzenia kompilacji, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Porady: określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Porady: określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)
