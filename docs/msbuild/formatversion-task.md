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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634113"
---
# <a name="formatversion-task"></a>FormatVersion, zadanie

Dołącza numer poprawki do numeru wersji.

- #1 przypadku: Input: Version =\<undefined >;  Poprawka =\<nie należy uważać >;   Wynik: OutputVersion = "1.0.0.0"

- #2 przypadku: Input: Version = "1.0.0. *" Revision = "5" Output: OutputVersion = "1.0.0.5"

- #3 przypadku: Input: Version = "1.0.0.0" Revision =\<nie należy uważać >;  Wynik: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `FormatVersion`.

|Parametr|Opis|
|---------------|-----------------|
|`FormatType`|Opcjonalny parametr `String`.<br /><br /> Określa typ formatu.<br /><br /> -"Version" = Version.<br />-"Path" = Zastąp "." znakiem "_";|
|`OutputVersion`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa wersję wyjściową, która zawiera numer poprawki.|
|`Revision`|Opcjonalny parametr `Int32`.<br /><br /> Określa poprawkę, która ma zostać dołączona do wersji.|
|`Version`|Opcjonalny parametr `String`.<br /><br /> Określa ciąg numeru wersji do sformatowania.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
