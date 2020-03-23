---
title: Klasa VCToolTask | Dokumenty firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591674"
---
# <a name="vctooltask-base-class"></a>VCToolZadniak klasa podstawowa

Wiele zadań ostatecznie <xref:Microsoft.Build.Utilities.Task> dziedziczyć z klasy i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) klasy. Ta klasa dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry klasy podstawowej **VCToolTask.**

|Parametr|Opis|
|---------------|-----------------|
|**ActiveToolSwitchesValues (Przełączniki ActiveToolSvalues)**|**Opcjonalny\<ciąg słownika, parametr ToolSwitch>.**|
|**Dodatkoweopcje**|Opcjonalny parametr **ciągu.**|
|**Efektywnyseksedirectory pracy**|Opcjonalny parametr **ciągu.**|
|**WłączErrorListRegex**|Opcjonalny parametr **bool.**<br/><br/>Wartość domyślna to `true`.|
|**Lista błędówRegex**|Opcjonalny parametr **ITaskItem[].**|
|**Lista błędówWydanie**|Opcjonalny parametr **ITaskItem[].**|
|**Generowaniekommandline**|Opcjonalny parametr **ciągu.**<br/><br/>Używa wartości **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] i **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Opcjonalny parametr **ciągu.**<br/><br/>Używa **wartości string[]** *switchesToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] i **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
