---
title: FormatVersion — zadanie | Microsoft Docs
description: Dowiedz się więcej na temat różnych sposobów, w których zadania programu MSBuild FormatVersion dołączają numer poprawki do numeru wersji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 16da018e49e6cb456074ebabac52a8768d06c1c6
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436703"
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
