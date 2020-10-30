---
title: Klasa VCToolTask | Microsoft Docs
description: Dowiedz się więcej na temat kilku parametrów, które Klasa bazowa VCToolTask dodaje do zadań, które dziedziczą.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046733"
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
|**GenerateCommandLineExceptSwitches**|Opcjonalny parametr **ciągu** .<br/><br/>Używa **ciągu wartości []** *switchesToRemove* , **CommandLineFormat** *Format* [default = CommandLineFormat. ForBuildLog] i **EscapeFormat** *EscapeFormat* [default = EscapeFormat. default].|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
