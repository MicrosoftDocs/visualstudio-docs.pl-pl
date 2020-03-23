---
title: TrackedVCToolTask Klasa | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594932"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask klasa podstawowa

Wiele zadań ostatecznie <xref:Microsoft.Build.Utilities.Task> dziedziczyć z klasy i [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) klasy. Ta klasa dodaje kilka parametrów do zadań, które pochodzą z [VCToolTask](../msbuild/vctooltask-base-class.md). Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry klasy podstawowej **TrackedVCToolTask.**

|Parametr|Opis|
|---------------|-----------------|
|**UsuńOutputOnExecute**|Opcjonalny parametr **bool.**|
|**EnableExecuteTool (Włącz)**|Opcjonalny parametr **bool.**|
|**ExcludedInputPaths (Ścieżki wykluczeń nieprzenikasłowych)**|Opcjonalny parametr **ITaskItem[].**|
|**MinimalRebuildFromTracking**|Opcjonalny parametr **bool.**|
|**ŚcieżkaOverride**|Opcjonalny parametr **ciągu.**|
|**PostBuildTrackingCleanup**|Opcjonalny parametr **bool.**|
|**Źródło danych RootSource**|Opcjonalny parametr **ciągu.**|
|**PominięteWykonaczenie**|Opcjonalny parametr wyjściowy **bool.**|
|**ŹródłaKomisowany**|Opcjonalny parametr **wyjściowy ITaskItem[].**|
|**Plik TLogCommand**|Opcjonalny parametr **ITaskItem.**|
|**TLogReadFiles**|Opcjonalny parametr **ITaskItem[].**|
|**TLogWriteFiles (Pliki TLogWriteFiles)**|Opcjonalny parametr **ITaskItem[].**|
|**ToolArchitecture (Etykieta narzędzia)**|Opcjonalny parametr **ciągu.**|
|**TrackCommandLines (Linie śledzenia ścieżek)**|Opcjonalny parametr **bool.**|
|**TrackFileAccess (Plik utworu)**|Opcjonalny parametr **bool.**|
|**TrackedInputFilesToIgnore**|Opcjonalny parametr **ITaskItem[].**|
|**TrackedOutputFilesToIgnore**|Opcjonalny parametr **ITaskItem[].**|
|**Ścieżka trackera**|Opcjonalny parametr **ciągu.**|
|**Ścieżka śledzenia**|Opcjonalny parametr **ciągu.**|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)<br/>
[Zadania](../msbuild/msbuild-tasks.md)
