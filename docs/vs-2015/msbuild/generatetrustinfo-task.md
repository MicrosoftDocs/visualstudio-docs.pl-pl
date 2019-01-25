---
title: Generatetrustinfo — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f1cf52286de97980eb269c3b52055be4455c38d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790155"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generuje zaufanie aplikacji z manifestu podstawowej oraz `TargetZone` i `ExcludedPermissions` parametrów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateTrustInfo` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationDependencies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawów zależnych.|  
|`BaseManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa podstawowy manifest można wygenerować zaufanie aplikacji z.|  
|`ExcludedPermissions`|Opcjonalnie `String` parametru.<br /><br /> Określa jedną lub więcej wartości tożsamości uprawnień rozdzieloną średnikami mają być wykluczone z zestawu uprawnień strefy domyślnej.|  
|`TargetZone`|Opcjonalnie `String` parametru.<br /><br /> Określa zestaw uprawnień strefy domyślnej, uzyskany od zasad komputera.|  
|`TrustInfoFile`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który zawiera informacje dotyczące relacji zaufania zabezpieczeń aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
