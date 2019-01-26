---
title: GetReferenceAssemblyPaths, zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 227b7ba739794bde1588dfbd3b04a5ba3a9e51d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989016"
---
# <a name="getreferenceassemblypaths-task"></a>Getreferenceassemblypaths — zadanie
Zwraca odwołanie ścieżki zestawów w różnych architektur.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GetReferenceAssemblyPaths` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Opcjonalnie `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie `TargetFrameworkMoniker` parametru. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalnie `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie `TargetFrameworkMoniker` parametru, bez uwzględniania częścią profilu moniker. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`TargetFrameworkMoniker`|Opcjonalnie `String` parametru.<br /><br /> Określa krótką nazwę platformy docelowej, który jest skojarzony z ścieżki zestawów odwołania.|  
|`RootPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżka katalogu głównego w celu wygenerowania ścieżki zestawów odwołania.|  
|`BypassFrameworkInstallChecks`|Opcjonalnie <xref:System.Boolean> parametru.<br /><br /> Jeśli `true`, pomija kontrole podstawowe, `GetReferenceAssemblyPaths` wykonuje domyślnie, aby upewnić się, że niektórych platform środowiska uruchomieniowego są zainstalowane, w zależności od platformy docelowej.|  
|`TargetFrameworkMonikerDisplayName`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę wyświetlaną dla krótką nazwę platformy docelowej.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)