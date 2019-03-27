---
title: TrackedVCToolTask Class | Microsoft Docs
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
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515444"
---
# <a name="trackedvctooltask-base-class"></a>Klasa bazowa TrackedVCToolTask

Wiele zadań, ale ostatecznie dziedziczyć <xref:Microsoft.Build.Utilities.Task> klasy i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) klasy. Ta klasa dodaje kilka parametrów do zadań, które wynikają z [VCToolTask](../msbuild/vctooltask-base-class.md). Te parametry są wymienione w niniejszym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **TrackedVCToolTask** klasy bazowej.

|Parametr|Opis|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Opcjonalnie **bool** parametru.|
|**EnableExecuteTool**|Opcjonalnie **bool** parametru.|
|**ExcludedInputPaths**|Opcjonalnie **[] ITaskItem** parametru.|
|**MinimalRebuildFromTracking**|Opcjonalnie **bool** parametru.|
|**PathOverride**|Opcjonalnie **ciąg** parametru.|
|**PostBuildTrackingCleanup**|Opcjonalnie **bool** parametru.|
|**RootSource**|Opcjonalnie **ciąg** parametru.|
|**SkippedExecution**|Opcjonalnie **bool** parametr wyjściowy.|
|**SourcesCompiled**|Opcjonalnie **[] ITaskItem** parametr wyjściowy.|
|**TLogCommandFile**|Opcjonalnie **ITaskItem** parametru.|
|**TLogReadFiles**|Opcjonalnie **[] ITaskItem** parametru.|
|**TLogWriteFiles**|Opcjonalnie **[] ITaskItem** parametru.|
|**ToolArchitecture**|Opcjonalnie **ciąg** parametru.|
|**TrackCommandLines**|Opcjonalnie **bool** parametru.|
|**TrackFileAccess**|Opcjonalnie **bool** parametru.|
|**TrackedInputFilesToIgnore**|Opcjonalnie **[] ITaskItem** parametru.|
|**TrackedOutputFilesToIgnore**|Opcjonalnie **[] ITaskItem** parametru.|
|**TrackerFrameworkPath**|Opcjonalnie **ciąg** parametru.|
|**TrackerSdkPath**|Opcjonalnie **ciąg** parametru.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)