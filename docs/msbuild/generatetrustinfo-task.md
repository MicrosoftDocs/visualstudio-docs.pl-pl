---
title: Generatetrustinfo — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2c4c03eba5d0b154ce219daeea3761a001a2198
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949579"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — zadanie
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
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)