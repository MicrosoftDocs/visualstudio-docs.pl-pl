---
title: XSD — zadanie | Dokumentacja firmy Microsoft
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78fe110ee6abf70d091f9d7c1f67b56608f82c27
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57982990"
---
# <a name="xsd-task"></a>XSD — Zadanie
Opakowuje narzędzie definicji schematu XML (*xsd.exe*), które generuje pliki schematu lub klasa ze źródła.

> [!NOTE]
> Począwszy od programu Visual Studio 2017 roku Obsługa projekt C++ *xsd.exe* jest przestarzała. Można nadal używać **Microsoft.VisualC.CppCodeProvider** interfejsów API, ręcznie dodając *CppCodeProvider.dll* w pamięci GAC.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry **XSD** zadania.

-   **AdditionalOptions**

     Opcjonalnie **ciąg** parametru.

     Lista opcji określonych w wierszu polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **XSD** parametru zadania.

-   **GenerateFromSchema**

     Opcjonalnie **ciąg** parametru.

     Określa typy, które są generowane na podstawie określonego schematu.

     Określ jedną z następujących wartości, z których każdy odpowiada opcji XSD.

    -   **classes** - **/classes**

    -   **dataset** - **/dataset**

-   **Język**

     Opcjonalnie **ciąg** parametru.

     Określa język programowania dla wygenerowanego kodu.

     Wybierz z **CS** (C#, co jest ustawieniem domyślnym), **VB** (Visual Basic) lub **JS** (JScript). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.

-   **Namespace**

     Opcjonalnie **ciąg** parametru.

     Określa przestrzeń nazw czasu wykonywania wygenerowany typów.

-   **Źródła**

     Wymagane `ITaskItem[]` parametru.

     Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.

-   **SuppressStartupBanner**

     Opcjonalnie **logiczna** parametru.

     Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.

-   **TrackerLogDirectory**

     Opcjonalnie **ciąg** parametru.

     Określa katalog dziennika śledzenia.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)