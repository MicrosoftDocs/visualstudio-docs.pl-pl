---
title: FormatVersion — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149616"
---
# <a name="formatversion-task"></a>FormatVersion — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dołącza numer poprawki do numeru wersji.  
  
- #1 przypadku: dane wejściowe: wersja = \<undefined> ;  Poprawka = \<don't care> ;   Wynik: OutputVersion = "1.0.0.0"  
  
- #2 przypadku: Input: Version = "1.0.0. *" Revision = "5" Output: OutputVersion = "1.0.0.5"  
  
- #3 przypadku: Input: Version = "1.0.0.0" Revision = \<don't care> ;  Wynik: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FormatVersion` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FormatType`|Opcjonalny `String` parametr.<br /><br /> Określa typ formatu.<br /><br /> -"Version" = Version.<br />-"Path" = Zastąp "." znakiem "_";|  
|`OutputVersion`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa wersję wyjściową, która zawiera numer poprawki.|  
|`Revision`|Opcjonalny `Int32` parametr.<br /><br /> Określa poprawkę, która ma zostać dołączona do wersji.|  
|`Version`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg numeru wersji do sformatowania.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
