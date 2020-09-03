---
title: Klasa bazowa ToolTaskExtension | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631695"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension, klasa podstawowa

Wiele zadań dziedziczy z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask> , która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry klas bazowych.

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.<br /><br /> Jest to wygodna właściwość, dzięki czemu autorzy zadań dziedziczą z tej klasy nie muszą rzutować wartości z `IBuildEngine` na `IBuildEngine2` . |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na wartość `true` to zadanie przekazuje wartość **/q** do *cmd.exe* wiersza polecenia, aby nie skopiować wiersza polecenia do strumienia stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalny `String` parametr tablicy.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Te zmienne są przesyłane do zduplikowanego pliku wykonywalnego, a także do selektywnego przesłaniania, zwykłego bloku środowiska. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie. Jeśli zadanie zarejestrował jakiekolwiek błędy, ale proces miał kod zakończenia 0 (sukces), jest to wartość-1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Opcjonalny <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli IDE hosta skojarzył obiekt hosta z tym konkretnym zadaniem. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Opcjonalny <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr tylko do odczytu.<br /><br /> Pobiera wystąpienie klasy zawierającej <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> metody rejestrowania zadań. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | `bool`Parametr opcji.<br /><br /> Jeśli `true` wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Wirtualny `Int32` parametr opcjonalny.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu. Limit czasu jest w milisekundach. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Wirtualny `string` parametr opcjonalny.<br /><br /> Projekty mogą zaimplementować ten element, aby zastąpić narzędzie. Zadania mogą zastąpić ten sposób, aby zachować wartość tego narzędzia. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Opcjonalny `string` parametr.<br /><br /> Określa lokalizację, z której zadanie ładuje źródłowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK, która odnosi się do wersji platformy, w której działa program MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na `true` , to zadanie tworzy plik wsadowy dla wiersza polecenia i wykonuje go przy użyciu procesora poleceń zamiast wykonywania polecenia bezpośrednio. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Opcjonalny `bool` parametr.<br /><br /> Gdy jest ustawiona na `true` , to zadanie daje węzeł, gdy jego zadanie jest wykonywane. |

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
