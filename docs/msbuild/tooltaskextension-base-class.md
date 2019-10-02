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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7734f852da997836cf2f42fd3f6b96e9decdf8dd
ms.sourcegitcommit: 628eb202a1153ebfe69c668f966f821b98b34b34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71720568"
---
# <a name="tooltaskextension-base-class"></a>Klasa bazowa ToolTaskExtension
Wiele zadań dziedziczy z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry klas bazowych.

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.<br /><br /> Jest to wygodna właściwość, dzięki czemu autorzy zadań dziedziczą z tej klasy nie muszą rzutować wartości z `IBuildEngine` na `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Opcjonalny `bool` parametr.<br /><br /> W przypadku ustawienia wartości `true` to zadanie przekazuje wartość **/q** do wiersza polecenia *cmd. exe* w taki sposób, że wiersz polecenia nie jest kopiowany do stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalny parametr tablicy `String`.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Te zmienne są przesyłane do zduplikowanego pliku wykonywalnego, a także do selektywnego przesłaniania, zwykłego bloku środowiska. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie. Jeśli zadanie zarejestrował jakiekolwiek błędy, ale proces miał kod zakończenia 0 (sukces), jest to wartość-1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Opcjonalny <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli IDE hosta skojarzył obiekt hosta z tym konkretnym zadaniem. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Opcjonalny parametr <xref:Microsoft.Build.Utilities.TaskLoggingHelper> tylko do odczytu.<br /><br /> Pobiera wystąpienie klasy <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> zawierającej metody rejestrowania zadań. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Opcja `bool` parametr.<br /><br /> Jeśli `true`, wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Wirtualny opcjonalny parametr `Int32`.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. Limit czasu jest w milisekundach. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Wirtualny opcjonalny parametr `string`.<br /><br /> Projekty mogą zaimplementować ten element, aby zastąpić narzędzie. Zadania mogą zastąpić ten sposób, aby zachować wartość tego narzędzia. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Opcjonalny `string` parametr.<br /><br /> Określa lokalizację, z której zadanie ładuje źródłowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK, która odnosi się do wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na `true` to zadanie tworzy plik wsadowy dla wiersza polecenia i wykonuje go przy użyciu procesora poleceń zamiast bezpośrednio wykonywać polecenie. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Opcjonalny `bool` parametr.<br /><br /> Ustawienie `true` spowoduje, że to zadanie nadaje węzeł, gdy jego zadanie jest wykonywane. |

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)