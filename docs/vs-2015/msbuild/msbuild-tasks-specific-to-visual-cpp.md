---
title: Zadania programu MSBuild specyficzne dla Visual C++ | Microsoft Docs
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
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686907"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Zadania narzędzia MSBuild właściwe dla Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Po zainstalowaniu Visual C++ są dostępne następujące zadania, oprócz tych, które są instalowane z programem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Aby uzyskać więcej informacji, zobacz [MSBuild (Visual C++) — Omówienie](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Oprócz parametrów dla każdego zadania, każde zadanie ma również następujące parametry.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Condition`|Opcjonalny `String` parametr.<br /><br /> `Boolean`Wyrażenie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używane przez aparat do określenia, czy zadanie zostanie wykonane. Aby uzyskać informacje na temat warunków, które są obsługiwane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] program, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametr opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.<br /><br /> Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[BscMake, zadanie](../msbuild/bscmake-task.md)|Pakuje narzędzie do konserwacji informacji przeglądarki Microsoft (bscmake.exe).|  
|[CL — zadanie](../msbuild/cl-task.md)|Zawija Visual C++ narzędzia kompilatora (cl.exe).|  
|[CPPClean —, zadanie](../msbuild/cppclean-task.md)|Usuwa pliki tymczasowe, które program MSBuild tworzy po skompilowaniu projektu Visual C++.|  
|[LIB — zadanie](../msbuild/lib-task.md)|Zawija narzędzie Microsoft 32-bit Library Manager (lib.exe).|  
|[Połącz zadanie](../msbuild/link-task.md)|Zawija Visual C++ narzędzia konsolidatora (link.exe).|  
|[MIDL, zadanie](../msbuild/midl-task.md)|Zawija Microsoft Interface Definition Language (midl.exe) narzędzie kompilatora (MIDL).|  
|[MT — zadanie](../msbuild/mt-task.md)|Zawija narzędzie manifestu firmy Microsoft (mt.exe).|  
|[RC — zadanie](../msbuild/rc-task.md)|Zawija narzędzie kompilatora zasobów systemu Microsoft Windows (rc.exe).|  
|[SetEnv, zadanie](../msbuild/setenv-task.md)|Ustawia lub usuwa wartość określonej zmiennej środowiskowej.|  
|[VCMessage —, zadanie](../msbuild/vcmessage-task.md)|Rejestruje komunikaty ostrzegawcze i komunikaty o błędach podczas kompilacji.|  
|[XDCMake, zadanie](../msbuild/xdcmake-task.md)|Zawija narzędzie dokumentacji XML (xdcmake.exe), które scala pliki komentarzy dokumentów XML (. xdc) w pliku XML.|  
|[Zadanie XSD](../msbuild/xsd-task.md)|Zawija narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy ze źródła.|  
|[Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)|Opisuje elementy systemu MSBuild.|  
|[Zadania](../msbuild/msbuild-tasks.md)|Opisuje zadania, które są jednostkami kodu, które można połączyć w celu utworzenia kompilacji.|  
|[Pisanie zadania](../msbuild/task-writing.md)|Opisuje sposób tworzenia zadania.|
