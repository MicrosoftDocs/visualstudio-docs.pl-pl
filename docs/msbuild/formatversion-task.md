---
title: Zadanie FormatVersion | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634113"
---
# <a name="formatversion-task"></a>Zadanie FormatVersion

Dołącza numer poprawki do numeru wersji.

- Przypadek #1: Wejście: Wersja\<= niezdefiniowana>;  Rewizja\<= nie obchodzi>;   Wyjście: OutputVersion="1.0.0.0"

- Przypadek #2: Wejście: Wersja="1.0.0.*" Revision="5" Wyjście: OutputVersion="1.0.0.5"

- Przypadek #3: Wejście: Version="1.0.0.0" Revision=\<nie obchodzi>;  Wyjście: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametry

 W poniższej tabeli `FormatVersion` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FormatType`|Parametr `String` opcjonalny.<br /><br /> Określa typ formatu.<br /><br /> - "Version" = wersja.<br />- "Ścieżka" = zastąpienie "." "_";|
|`OutputVersion`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa wersję wyjściową zawierającą numer poprawki.|
|`Revision`|Parametr `Int32` opcjonalny.<br /><br /> Określa poprawkę, która ma być dołączona do wersji.|
|`Version`|Parametr `String` opcjonalny.<br /><br /> Określa ciąg numeru wersji do formatowania.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
