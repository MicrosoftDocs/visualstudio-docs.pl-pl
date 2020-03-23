---
title: 'Wiersz polecenia profilera: Instrument .NET service, get timing detail'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: af801d2b30c48deb1a88800f67ff4d3efef412b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778898"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Instrukcje: instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera

W tym artykule opisano sposób używania narzędzi wiersza polecenia Narzędzi programu Visual Studio Profiling Tools do inrządowania usługi .NET Framework i zbierania szczegółowych danych chronometrażu.

> [!NOTE]
> Nie można profilować usługi przy użyciu metody instrumentacji, jeśli nie można ponownie uruchomić usługi po uruchomieniu komputera, takiej usługi, która uruchamia się tylko po uruchomieniu systemu operacyjnego.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.
>
> Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. Zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Aby zebrać szczegółowe dane chronometrażu z usługi .NET Framework przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania instrumentalnej wersji składnika. Następnie należy zastąpić nieprzyrządwioną wersję usługi wersją instrumentamenczną, upewniając się, że usługa jest skonfigurowana do ręcznego uruchamiania. Narzędzie [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) służy do inicjowania zmiennych środowiska profilowania globalnego, a następnie ponownego uruchamiania komputera-hosta. Następnie należy uruchomić profiler.

Po uruchomieniu usługi dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymać i wznowić zbieranie danych.

Aby zakończyć sesję profilowania, należy wyłączyć usługę, a następnie jawnie zamknąć profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera

1. Otwórz okno wiersza polecenia.

2. Użyj **narzędzia VSInstr** do generowania instrumentowanych wersji usługi binarnej.

3. Zastąp oryginalny plik binarny wersją instrumentamencie. W Menedżerze sterowania usługami systemu Windows upewnij się, że typ uruchamiania usługi jest ustawiony na Ręczny.

4. Inicjowanie zmiennych środowiskowych profilowania programu .NET Framework. Wpisz:

     **VSPerfClrEnv /globaltraceon**

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom profiler. Wpisz:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:trace** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację danych profilowania (.* vsp).*

     Można użyć dowolnej z następujących opcji z **/start:trace** opcji.

     > [!NOTE]
     > Opcje **/user** i **/crosssession** są zwykle wymagane dla usług profilowania.

     | Opcja | Opis |
     | - | - |
     | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
     | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **Procesy** Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
     | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przez profiler, zanim zwróci błąd. Jeśli `Interval` nie zostanie określony, profiler czeka przez czas nieokreślony. Domyślnie **/start** zwraca natychmiast. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymaną kolekcją danych, dodaj opcję **/globaloff** do wiersza polecenia **/start.** Użyj **/globalon,** aby wznowić profilowanie. |
     | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w configu. Informacje o liczniku są dodawane do danych zebranych podczas każdego zdarzenia profilowania. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

8. Uruchom usługę z Menedżera sterowania usługami systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy usługa jest uruchomiona, można użyć opcji *PROGRAMU VSPerfCmd.exe,* aby rozpocząć i zatrzymać zapisywanie danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie usługi.

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych`TID`dla wątku określonego przez identyfikator wątku ( ).|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania

Aby zakończyć sesję profilowania, zatrzymaj usługę, która jest uruchomiona instrumentowany składnik, a następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. **Polecenie VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania.

Należy ponownie uruchomić komputer, aby można było zastosować nowe ustawienia środowiska.

1. Zatrzymaj usługę z Menedżera sterowania usługami.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

3. Po zakończeniu profilowania wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Wymień moduł oprzyrządowany na oryginalny. W razie potrzeby ponownie skonfiguruj typ uruchomienia usługi.

5. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też

[Profile services](../profiling/command-line-profiling-of-services.md)
[Instrumentation method data views](../profiling/instrumentation-method-data-views.md)
