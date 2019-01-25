---
title: XSD — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c8e38959e9835ee26f283c59128749239178307
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778727"
---
# <a name="xsd-task"></a>XSD — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Opakowuje narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy z lokalizacji źródłowej.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **XSD** zadania.  
  
-   **AdditionalOptions**  
  
     Opcjonalnie **ciąg** parametru.  
  
     Lista opcji określonych w wierszu polecenia. Na przykład "*/option1 /option2 /option#*". Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **XSD** parametru zadania.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
