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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58071162"
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