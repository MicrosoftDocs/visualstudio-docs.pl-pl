---
title: Requiresframework35sp1assembly — — zadanie | Microsoft Docs
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
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ada207a619021922b999d0e821ecf27ba48dbb38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158739"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RequiresFramework35SP1Assembly` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy, do których odwołuje się aplikacja.|  
|`CreateDesktopShortcut`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` program utworzy ikonę skrótu na pulpicie podczas instalacji.|  
|`DeploymentManifestEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa nazwę pliku manifestu aplikacji.|  
|`EntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa zestaw, który ma zostać wykonany po uruchomieniu aplikacji.|  
|`ErrorReportUrl`|Opcjonalny `String` parametr.<br /><br /> Określa witrynę sieci Web, która jest wyświetlana w oknach dialogowych, które są dostępne podczas instalacji ClickOnce.|  
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa listę plików, które zostaną wdrożone po opublikowaniu aplikacji.|  
|`ReferencedAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy, do których odwołuje się projekt.|  
|`RequiresMinimumFramework35SP1`|Opcjonalny `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true` aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.|  
|`SigningManifests`|Opcjonalny `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true` manifesty ClickOnce są podpisane.|  
|`SuiteName`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę folderu w menu **Start** , w którym zostanie zainstalowana aplikacja.|  
|`TargetFrameworkVersion`|Opcjonalny `String` parametr.<br /><br /> Określa wersję .NET Framework, do której odwołuje się ta aplikacja.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
