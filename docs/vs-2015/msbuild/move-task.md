---
title: Przenieś zadanie | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191571"
---
# <a name="move-task"></a>Move — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przenosi pliki do nowej lokalizacji.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujące kwestie opisano parametry `Move` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa listę plików, do których mają zostać przeniesione pliki źródłowe. Ta lista powinna być mapowaniem jeden-do-jednego do listy określonej w `SourceFiles` parametrze. Oznacza to, że pierwszy plik określony w programie `SourceFiles` zostanie przeniesiony do pierwszej lokalizacji określonej w `DestinationFiles` i tak dalej.|  
|`DestinationFolder`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa katalog, do którego chcesz przenieść pliki.|  
|`MovedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały pomyślnie przeniesione.|  
|`OverwriteReadOnlyFiles`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zastępuje pliki, nawet jeśli są oznaczone jako pliki tylko do odczytu.|  
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do przeniesienia.|  
  
## <a name="remarks"></a>Uwagi  
 `DestinationFolder` `DestinationFiles` Należy określić parametr lub parametr, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.  
  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
