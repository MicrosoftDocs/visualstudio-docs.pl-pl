---
title: Klasa VCToolTask | Dokumentacja firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970721"
---
# <a name="vctooltask-base-class"></a>Klasa bazowa VCToolTask

Wiele zadań, ale ostatecznie dziedziczyć <xref:Microsoft.Build.Utilities.Task> klasy i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) klasy. Ta klasa dodaje kilka parametrów do zadań, które wynikają z nich. Te parametry są wymienione w niniejszym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **VCToolTask** klasy bazowej.

|Parametr|Opis|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Opcjonalnie **słownika\<ciągu ToolSwitch >** parametru.|
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.|
|**EffectiveWorkingDirectory**|Opcjonalnie **ciąg** parametru.|
|**EnableErrorListRegex**|Opcjonalnie **bool** parametru.<br/><br/>Wartość domyślna to `true`.|
|**ErrorListRegex**|Opcjonalnie **[] ITaskItem** parametru.|
|**ErrorListListExclusion**|Opcjonalnie **[] ITaskItem** parametru.|
|**GenerateCommandLine**|Opcjonalnie **ciąg** parametru.<br/><br/>Używa wartości **CommandLineFormat** *format* [domyślna = CommandLineFormat.ForBuildLog] i **EscapeFormat** *escapeFormat* [ domyślne = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Opcjonalnie **ciąg** parametru.<br/><br/>Używa wartości **string []** *switchesToRemove*, **CommandLineFormat** *format* [domyślna = CommandLineFormat.ForBuildLog], a **EscapeFormat** *escapeFormat* [domyślna = EscapeFormat.Default].|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)