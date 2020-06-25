---
title: Wiersz polecenia profilera-Instrumentacja usługi .NET, Pobierz szczegóły chronometrażu
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 62303ab2ea7296ca5093636efcf97ea7a3c540c1
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331482"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Instrukcje: instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera

W tym artykule opisano sposób korzystania z narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania do Instrumentacji usługi .NET Framework i zbierania szczegółowych danych o chronometrażu.

> [!NOTE]
> Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie może zostać uruchomiona ponownie po uruchomieniu komputera, taka usługa, która jest uruchamiana tylko podczas uruchamiania systemu operacyjnego.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędziami profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Aby zebrać szczegółowe dane o chronometrażu z usługi .NET Framework przy użyciu metody instrumentacji, można użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika. Następnie należy zamienić nieinstrumentację wersję usługi na wersję instrumentacji, upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Użyj narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować globalne zmienne środowiskowe profilowania, a następnie ponownie uruchom komputer hosta. Następnie uruchamiasz Profiler.

Po uruchomieniu usługi dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

Aby zakończyć sesję profilowania, Wyłącz usługę, a następnie jawnie wyłącz Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** , aby wygenerować instrumentację wersji pliku binarnego usługi.

3. Zamień oryginalny plik binarny na wersję z instrumentacją. W Menedżerze sterowania usługami systemu Windows upewnij się, że typ uruchamiania usługi jest ustawiony na ręczny.

4. Zainicjuj zmienne środowiskowe profilowania .NET Framework. Wpisz:

     **VSPerfClrEnv/globaltraceon**

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom Profiler. Wpisz:

     **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]

   - Opcja [/Start](../profiling/start.md)**: Trace** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile`Określa nazwę i lokalizację danych profilowania (.* VSP*).

     Można użyć jednej z następujących opcji z opcją **/Start: Trace** .

     > [!NOTE]
     > Opcje **/User** i **/CrossSession** są zwykle wymagane do profilowania usług.

     | Opcja | Opis |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
     | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
     | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Określa liczbę sekund oczekiwania na zainicjowanie profilera przed zwróceniem błędu. Jeśli `Interval` nie jest określony, profiler czeka na czas nieokreślony. Domyślnie **/Start** zwraca natychmiast. |
     | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** . |
     | [/Counter](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w konfiguracji. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
     | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |

8. Uruchom usługę za pomocą Menedżera kontroli usług systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy usługa jest uruchomiona, możesz użyć opcji *VSPerfCmd.exe* , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie usługi.

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub kończy (**/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku ( `TID` ).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania

Aby zakończyć sesję profilowania, Zatrzymaj usługę, na której działa składnik instrumentacji, a następnie Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/GlobalOff** czyści zmienne środowiskowe profilowania.

Aby zastosować nowe ustawienia środowiska, należy ponownie uruchomić komputer.

1. Zatrzymaj usługę z menedżera kontroli usług.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Po ukończeniu wszystkich profilowania Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/GlobalOff**

4. Zamień moduł z pakietem na oryginalny. W razie potrzeby skonfiguruj ponownie typ uruchomienia usługi.

5. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też

[Usługi profilu](../profiling/command-line-profiling-of-services.md) 
 [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
