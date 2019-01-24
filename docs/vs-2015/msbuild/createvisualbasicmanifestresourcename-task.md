---
title: CreateVisualBasicManifestResourceName Task | Microsoft Docs
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d49f47a935f82d1c03af9faad941470107e2eca6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761659"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]— styl nazwy manifestu z nazwę pliku ResX danego lub innego zasobu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` Parametr tylko do odczytu danych wyjściowych.<br /><br /> Wynikowy nazwy manifestu.|  
|`ResourceFiles`|Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobów, z której ma zostać utworzona [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nazwy manifestu.|  
|`RootNamespace`|Opcjonalnie `String` parametru.<br /><br /> Przestrzeń nazw głównego pliku zasobów, zwykle pobierane z pliku projektu. Może być `null`.|  
|`PrependCultureAsDirectory`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawany jako nazwę katalogu, tuż przed nazwę zasobu manifestu. Wartość domyślna to `true`.|  
|`ResourceFilesWithManifestResourceNames`|Opcjonalnie, tylko do odczytu `String` parametr wyjściowy.<br /><br /> Zwraca nazwę pliku zasobu, który teraz zawiera nazwę zasobu manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę odpowiedniego zasobu manifestu, można przypisać do danej resx lub inny plik zasobów. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jako metadane.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
