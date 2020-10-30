---
title: Klasa TrackedVCToolTask | Microsoft Docs
description: Dowiedz się więcej na temat parametrów, które Klasa bazowa TrackedVCToolTask dodaje do zadań, które dziedziczą.
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046995"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask, klasa podstawowa

Wiele zadań ostatecznie dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task> Class i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Ta klasa dodaje kilka parametrów do zadań, które pochodzą od [VCToolTask](../msbuild/vctooltask-base-class.md). Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry klasy bazowej **TrackedVCToolTask** .

|Parametr|Opis|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Opcjonalny parametr **bool** .|
|**EnableExecuteTool**|Opcjonalny parametr **bool** .|
|**ExcludedInputPaths**|Opcjonalny parametr **ITaskItem []** .|
|**MinimalRebuildFromTracking**|Opcjonalny parametr **bool** .|
|**PathOverride**|Opcjonalny parametr **ciągu** .|
|**PostBuildTrackingCleanup**|Opcjonalny parametr **bool** .|
|**RootSource**|Opcjonalny parametr **ciągu** .|
|**SkippedExecution**|Opcjonalny parametr wyjściowy **bool** .|
|**SourcesCompiled**|Opcjonalny parametr wyjściowy **ITaskItem []** .|
|**TLogCommandFile**|Opcjonalny parametr **ITaskItem** .|
|**TLogReadFiles**|Opcjonalny parametr **ITaskItem []** .|
|**TLogWriteFiles**|Opcjonalny parametr **ITaskItem []** .|
|**ToolArchitecture**|Opcjonalny parametr **ciągu** .|
|**TrackCommandLines**|Opcjonalny parametr **bool** .|
|**TrackFileAccess**|Opcjonalny parametr **bool** .|
|**TrackedInputFilesToIgnore**|Opcjonalny parametr **ITaskItem []** .|
|**TrackedOutputFilesToIgnore**|Opcjonalny parametr **ITaskItem []** .|
|**TrackerFrameworkPath**|Opcjonalny parametr **ciągu** .|
|**TrackerSdkPath**|Opcjonalny parametr **ciągu** .|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
