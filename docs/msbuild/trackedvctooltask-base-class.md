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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594932"
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
