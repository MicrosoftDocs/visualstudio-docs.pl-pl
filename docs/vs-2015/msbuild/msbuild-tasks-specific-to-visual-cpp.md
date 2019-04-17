---
title: Program MSBuild zadania właściwe dla Visual C++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f4de01af6535a33607e5263966492210f8ce4a5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647966"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Zadania narzędzia MSBuild właściwe dla Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania zapewniają kod, który jest uruchamiany w procesie kompilacji. Po zainstalowaniu programu Visual C++, następujące zadania są dostępne, oprócz tych, które są instalowane z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Aby uzyskać więcej informacji, zobacz [Przegląd MSBuild (Visual C++)](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Oprócz parametrów dla każdego zadania każde zadanie ma następujące parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalnie `String` parametru.<br /><br /> A `Boolean` wyrażenia, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat używa do określenia, czy to zadanie zostanie wykonany. Aby uzyskać informacje o warunkach, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` elementu i kompilacja będą wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na`Target` elementu i kompilacja nie są wykonywane i całą `Target` elementu i kompilacja są traktowane jako zakończone niepowodzeniem.<br /><br /> Wersje programu .NET Framework przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[BscMake, zadanie](../msbuild/bscmake-task.md)|Opakowuje Microsoft Przeglądaj informacje narzędzie konserwacji (bscmake.exe).|  
|[CL, zadanie](../msbuild/cl-task.md)|Opakowuje narzędzia kompilatora Visual C++ (cl.exe).|  
|[CPPClean, zadanie](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, utworzone przez program MSBuild podczas kompilowania projektu Visual C++.|  
|[LIB, zadanie](../msbuild/lib-task.md)|Opakowuje narzędzie Microsoft 32-bitowy Library Manager (lib.exe).|  
|[Link, zadanie](../msbuild/link-task.md)|Opakowuje narzędzia konsolidatora Visual C++ (link.exe).|  
|[MIDL, zadanie](../msbuild/midl-task.md)|Opakowuje narzędzie kompilatora języka definicji interfejsu Microsoft (MIDL) (midl.exe).|  
|[MT, zadanie](../msbuild/mt-task.md)|Opakowuje narzędzie Microsoft manifestu (mt.exe).|  
|[RC, zadanie](../msbuild/rc-task.md)|Opakowuje narzędzie kompilatora zasobów systemu Microsoft Windows (rc.exe).|  
|[SetEnv, zadanie](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość określonej zmiennej środowiskowej.|  
|[VCMessage, zadanie](../msbuild/vcmessage-task.md)|Dzienniki ostrzeżenie wiadomości i komunikaty o błędach podczas kompilacji.|  
|[XDCMake, zadanie](../msbuild/xdcmake-task.md)|Opakowuje narzędzie dokumentacji XML (xdcmake.exe), które scala pliki komentarzy (.xdc) dokumentu XML w pliku XML.|  
|[XSD, zadanie](../msbuild/xsd-task.md)|Opakowuje narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy z lokalizacji źródłowej.|  
|[Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)|Opisano elementy systemu MSBuild.|  
|[Zadania](../msbuild/msbuild-tasks.md)|W tym artykule opisano zadania, które są jednostkami kod, który można łączyć, aby utworzyć kompilację.|  
|[Wpisywanie zadania](../msbuild/task-writing.md)|W tym artykule opisano sposób tworzenia zadania.|
