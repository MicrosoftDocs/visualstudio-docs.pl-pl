---
title: ToolTaskExtension, klasa podstawowa | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 061d78a1e6415d6e7386fdc4de76aa1dd8ddd6d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938918"
---
# <a name="tooltaskextension-base-class"></a>Tooltaskextension — klasa bazowa
Wiele zadań, o których dziedziczy <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które wynikają z nich. Te parametry są wymienione w niniejszym dokumencie.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry klas bazowych.

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine> parametru.<br /><br /> Określa dostępne dla zadań interfejsu aparatu kompilacji. Aparat kompilacji automatycznie ustawia tego parametru, aby zezwolić na wywołania zwrotnego do niego zadań. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine2> parametru.<br /><br /> Określa dostępne dla zadań interfejsu aparatu kompilacji. Aparat kompilacji automatycznie ustawia tego parametru, aby zezwolić na wywołania zwrotnego do niego zadań.<br /><br /> Jest to właściwość wygody, tak aby autorzy zadań dziedziczenie z tej klasy będą musieli rzutować wartości z `IBuildEngine` do `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine3> parametru.<br /><br /> Określa interfejs aparat kompilacji, które są udostępniane przez hosta. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Opcjonalnie `bool` parametru.<br /><br /> Po ustawieniu `true`, to zadanie przekazuje **/q** do *cmd.exe* wiersza polecenia w taki sposób, że w wierszu polecenia nie uzyskać skopiowane do strumienia wyjściowego stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalnie `String` tablicy parametrów.<br /><br /> Tablica par zmiennych środowiskowych, oddzielone znaku równości. Te zmienne są Powodzenie do pliku wykonywalnego zduplikowanych oprócz "lub" selektywnie nadrzędnych blok regularnych środowiska. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalnie `Int32` parametr tylko do odczytu danych wyjściowych.<br /><br /> Określa kod zakończenia, dostarczone przez wykonanego polecenia. Jeśli zadanie rejestrowane wszystkie błędy, ale proces ma kod zakończenia 0 (Powodzenie), to jest ustawiona na wartość -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskHost> parametru.<br /><br /> Określa wystąpienie obiektu hosta (może być null). Aparat kompilacji ustawia tę właściwość, jeśli host IDE skojarzył obiekt hosta tego konkretnego zadania. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Opcjonalnie <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametru tylko do odczytu.<br /><br /> Pobiera wystąpienie elementu <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> klasę, która zawiera metody rejestrowania zadań. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Opcja `bool` parametru.<br /><br /> Jeśli `true`, wszystkie komunikaty odebrane na Standardowy strumień błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Opcjonalnie `String` parametru.<br /><br /> Ważność, z którą ma zostać tekst dziennika od planu standard out strumienia. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Opcjonalnie `String` parametru.<br /><br /> Ważność, z którą ma zostać tekst dziennika od planu standard out strumienia. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Opcjonalne wirtualnej `Int32` parametru.<br /><br /> Określa ilość czasu w milisekundach, po których zostanie zakończony wykonywalnego zadania podrzędnego. Wartość domyślna to `Int.MaxValue`, wskazujący, że nie okres limitu czasu. Limit czasu wynosi (w milisekundach). |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Opcjonalne wirtualnej `string` parametru.<br /><br /> Projekty mogą implementować ten element, aby zastąpić ToolName. Zadania mogą zastąpić ten element, aby zachować ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Opcjonalnie `string` parametru.<br /><br /> Określa lokalizację, z którym zadanie ładowania podstawowego pliku wykonywalnego. Jeśli nie określono tego parametru, zadanie używa ścieżki instalacji zestawu SDK, odpowiadającą wersję framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Opcjonalnie `bool` parametru.<br /><br /> Po ustawieniu `true`, to zadanie tworzy plik wsadowy, w wierszu polecenia i uruchamia go przy użyciu procesora poleceń zamiast bezpośrednio wykonywania polecenia. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Opcjonalnie `bool` parametru.<br /><br /> Po ustawieniu `true`, to zadanie daje węzła, gdy jego zadanie jest wykonywane. |

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)