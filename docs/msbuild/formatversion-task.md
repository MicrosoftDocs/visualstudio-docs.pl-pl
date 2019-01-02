---
title: FormatVersion, zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f9b2cf2daff750f626f35b8c98f8269577b4099
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934073"
---
# <a name="formatversion-task"></a>Formatversion — zadanie
Dołącza numer wersji do numeru wersji.  
  
-   Przypadek #1: Dane wejściowe: Wersja =\<niezdefiniowana >;  Poprawka =\<nieważne >;   Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
-   Przypadek #2: Dane wejściowe: Wersja = poprawkę "1.0.0.*" = "5" w danych wyjściowych: OutputVersion = "1.0.0.5"  
  
-   W przypadku #3: Dane wejściowe: Wersja = "1.0.0.0" poprawki =\<nieważne >;  Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FormatVersion` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FormatType`|Opcjonalnie `String` parametru.<br /><br /> Określa typ formatu.<br /><br /> -"Wersja" = wersji.<br />-"Path"= Zastąp"." znakiem "_";|  
|`OutputVersion`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa numer wersji danych wyjściowych, który zawiera numer wersji.|  
|`Revision`|Opcjonalnie `Int32` parametru.<br /><br /> Określa poprawkę do dołączenia do wersji.|  
|`Version`|Opcjonalnie `String` parametru.<br /><br /> Określa ciąg numer wersji do sformatowania.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)