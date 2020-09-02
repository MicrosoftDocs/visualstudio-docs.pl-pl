---
title: Klasa VCToolTask | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591674"
---
# <a name="vctooltask-base-class"></a>VCToolTask, klasa podstawowa

Wiele zadań ostatecznie dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task> Class i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Ta klasa dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry klasy bazowej **VCToolTask** .

|Parametr|Opis|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Opcjonalny **parametr \<string, ToolSwitch> słownika** .|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .|
|**EffectiveWorkingDirectory**|Opcjonalny parametr **ciągu** .|
|**EnableErrorListRegex**|Opcjonalny parametr **bool** .<br/><br/>Wartość domyślna to `true`.|
|**ErrorListRegex**|Opcjonalny parametr **ITaskItem []** .|
|**ErrorListListExclusion**|Opcjonalny parametr **ITaskItem []** .|
|**GenerateCommandLine**|Opcjonalny parametr **ciągu** .<br/><br/>Używa wartości **CommandLineFormat** *Format* CommandLineFormat [default = CommandLineFormat. ForBuildLog] i **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|
|**GenerateCommandLineExceptSwitches**|Opcjonalny parametr **ciągu** .<br/><br/>Używa **ciągu wartości []** *switchesToRemove*, **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] i **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
