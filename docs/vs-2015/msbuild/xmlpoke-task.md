---
title: XmlPoke — — zadanie | Microsoft Docs
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
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ba57c1578bd69d71ed0abdac45907d937b89ecb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198967"
---
# <a name="xmlpoke-task"></a>XmlPoke — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawia wartości określone przez zapytanie XPath w pliku XML.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XmlPoke` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Namespaces`|Opcjonalny `String` parametr.<br /><br /> Określa przestrzenie nazw dla prefiksów zapytania XPath.|  
|`Query`|Opcjonalny `String` parametr.<br /><br /> Określa zapytanie XPath.|  
|`Value`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik wyjściowy.|  
|`XmlInputPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa dane wejściowe w formacie XML jako ścieżkę pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
