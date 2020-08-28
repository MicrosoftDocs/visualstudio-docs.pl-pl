---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042889"
---
### <a name="tooltaskextension-parameters"></a>Parametry ToolTaskExtension

To zadanie dziedziczy z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask> , która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich.

W poniższej tabeli opisano parametry klas bazowych:

| Parametr | Opis |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na wartość `true` to zadanie przekazuje wartość **/q** do *cmd.exe* wiersza polecenia, aby nie skopiować wiersza polecenia do strumienia stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Opcjonalny `String` parametr tablicy.<br /><br /> Tablica definicji zmiennych środowiskowych, oddzielonych średnikami. Każda definicja powinna określać nazwę zmiennej środowiskowej i wartość oddzieloną znakiem równości. Te zmienne są przesyłane do zduplikowanego pliku wykonywalnego, a także do selektywnego przesłaniania, zwykłego bloku środowiska. Na przykład `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie. Jeśli zadanie zarejestrował jakiekolwiek błędy, ale proces miał kod zakończenia 0 (sukces), jest to wartość-1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | `bool`Parametr opcji.<br /><br /> Jeśli `true` wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Opcjonalny `bool` parametr.<br /><br /> Jeśli `true` wszystkie komunikaty odebrane w standardowym strumieniu błędów są rejestrowane jako błędy. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Opcjonalny `String` parametr.<br /><br /> Znaczenie, za pomocą którego można rejestrować tekst ze standardowego strumienia wyjściowego. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu. Limit czasu jest w milisekundach. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Opcjonalny `string` parametr.<br /><br /> Projekty mogą zaimplementować ten element, aby zastąpić narzędzie. Zadania mogą zastąpić ten sposób, aby zachować wartość tego narzędzia. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Opcjonalny `string` parametr.<br /><br /> Określa lokalizację, z której zadanie ładuje źródłowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK, która odnosi się do wersji platformy, w której działa program MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Opcjonalny `bool` parametr.<br /><br /> Po ustawieniu na `true` , to zadanie tworzy plik wsadowy dla wiersza polecenia i wykonuje go przy użyciu procesora poleceń zamiast wykonywania polecenia bezpośrednio. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Opcjonalny `bool` parametr.<br /><br /> Gdy jest ustawiona na `true` , to zadanie daje węzeł, gdy jego zadanie jest wykonywane. |
