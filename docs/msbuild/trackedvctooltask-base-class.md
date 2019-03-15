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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 92d12e08f374efd306589d9d50f840a8d36f5b5a
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58071170"
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