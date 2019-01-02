---
title: Formaturl — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6086c03d3dae5a919b9b30abaecf2957076631b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845476"
---
# <a name="formaturl-task"></a>FormatUrl — zadanie
Konwertuje adres URL do poprawnego formatu adresu URL.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FormatUrl` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`InputUrl`|Opcjonalnie `String` parametru.<br /><br /> Określa adres URL do sformatowania.|  
|`OutputUrl`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa sformatowanym adresem URL.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)