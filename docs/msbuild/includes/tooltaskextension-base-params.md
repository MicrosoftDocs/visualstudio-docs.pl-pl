---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 38ac6925e98f4eb17b57d083c45977cb3f0f29ea
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167305"
---
### <a name="tooltaskextension-parameters"></a>Parametry ToolTaskExtension

To zadanie dziedziczy z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich.

W poniższej tabeli opisano parametry klas bazowych:

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na `true`wartość to zadanie przekazuje wartość **/q** do wiersza polecenia *cmd. exe* , tak aby wiersz polecenia nie był kopiowany do stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalny `String` parametr tablicy.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Te zmienne są przesyłane do zduplikowanego pliku wykonywalnego, a także do selektywnego przesłaniania, zwykłego bloku środowiska. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie. Jeśli zadanie zarejestrował jakiekolwiek błędy, ale proces miał kod zakończenia 0 (sukces), jest to wartość-1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parametr `bool` opcji.<br /><br /> Jeśli `true`wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Opcjonalny `bool` parametr.<br /><br /> Jeśli `true`wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. Limit czasu jest w milisekundach. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Opcjonalny `string` parametr.<br /><br /> Projekty mogą zaimplementować ten element, aby zastąpić narzędzie. Zadania mogą zastąpić ten sposób, aby zachować wartość tego narzędzia. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Opcjonalny `string` parametr.<br /><br /> Określa lokalizację, z której zadanie ładuje źródłowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK, która odnosi się do wersji platformy, w której działa program MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na `true`, to zadanie tworzy plik wsadowy dla wiersza polecenia i wykonuje go przy użyciu procesora poleceń zamiast wykonywania polecenia bezpośrednio. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Opcjonalny `bool` parametr.<br /><br /> Gdy jest ustawiona `true`na, to zadanie daje węzeł, gdy jego zadanie jest wykonywane. |
