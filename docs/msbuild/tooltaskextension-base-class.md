---
title: Klasa podstawowa ToolTaskExtension | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa052a0fd2216d5f3d85e99794d9ac883a09e2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631695"
---
# <a name="tooltaskextension-base-class"></a>Klasa podstawowa ToolTaskExtension

Wiele zadań dziedziczy z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która dziedziczy z klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry klas podstawowych.

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Parametr <xref:Microsoft.Build.Framework.IBuildEngine> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby umożliwić zadania do wywołania z powrotem do niego. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Parametr <xref:Microsoft.Build.Framework.IBuildEngine2> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby umożliwić zadania do wywołania z powrotem do niego.<br /><br /> Jest to właściwość wygody, dzięki czemu autorzy zadań dziedziczący z tej klasy nie muszą przerzucać wartości z `IBuildEngine` do `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Parametr <xref:Microsoft.Build.Framework.IBuildEngine3> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Parametr `bool` opcjonalny.<br /><br /> Po `true`ustawieniu, to zadanie przekazuje **/Q** do wiersza polecenia *cmd.exe* w taki sposób, że wiersz polecenia nie jest kopiowany do stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalny `String` parametr tablicy.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Zmienne te są przekazywane do zduplikowanego pliku wykonywalnego oprócz lub selektywnie nadrzędnego bloku zwykłego środowiska. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalny `Int32` parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie. Jeśli zadanie zarejestrowało błędy, ale proces miał kod zakończenia 0 (sukces), jest to ustawione na -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Parametr <xref:Microsoft.Build.Framework.ITaskHost> opcjonalny.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli ide hosta skojarzył obiekt hosta z tym konkretnym zadaniem. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Opcjonalny <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr tylko do odczytu.<br /><br /> Pobiera wystąpienie <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> klasy, która zawiera metody rejestrowania zadań. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametr `bool` opcji.<br /><br /> Jeśli `true`wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Parametr `String` opcjonalny.<br /><br /> Znaczenie, z którym można rejestrować tekst ze standardowego strumienia out. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Parametr `String` opcjonalny.<br /><br /> Znaczenie, z którym można rejestrować tekst ze standardowego strumienia out. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Wirtualny `Int32` parametr opcjonalny.<br /><br /> Określa czas w milisekundach, po upływie którego plik wykonywalny zadania zostanie zakończony. Wartością domyślną jest `Int.MaxValue`, wskazując, że nie ma okresu przeoczynia. Limit czasu jest w milisekundach. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Wirtualny `string` parametr opcjonalny.<br /><br /> Projekty mogą zaimplementować to, aby zastąpić ToolName. Zadania mogą zastąpić to, aby zachować ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Parametr `string` opcjonalny.<br /><br /> Określa lokalizację, z której zadanie ładuje podstawowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji SDK, która odpowiada wersji struktury, która jest uruchomiona MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Parametr `bool` opcjonalny.<br /><br /> Po ustawieniu `true`tego zadania tworzy plik wsadowy dla wiersza polecenia i wykonuje go za pomocą procesora poleceń zamiast wykonywania polecenia bezpośrednio. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Parametr `bool` opcjonalny.<br /><br /> Po ustawieniu `true`na , to zadanie daje węzeł, gdy jego zadanie jest wykonywane. |

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
