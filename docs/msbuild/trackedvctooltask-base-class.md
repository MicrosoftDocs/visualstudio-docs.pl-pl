---
title: Klasa TrackedVCToolTask | Microsoft Docs
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
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594932"
---
# <a name="trackedvctooltask-base-class"></a>Klasa bazowa TrackedVCToolTask

Wiele zadań ostatecznie dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task> i klasy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Ta klasa dodaje kilka parametrów do zadań, które pochodzą od [VCToolTask](../msbuild/vctooltask-base-class.md). Te parametry są wymienione w tym dokumencie.

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

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
