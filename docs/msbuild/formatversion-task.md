---
title: FormatVersion — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 250c73ce0395f278b72c18605f1666290670e20a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634113"
---
# <a name="formatversion-task"></a>FormatVersion, zadanie

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

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
