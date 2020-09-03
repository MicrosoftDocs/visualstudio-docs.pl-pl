---
title: Wiersz polecenia profilera — usługa natywna instrumentacji, pobieranie danych chronometrażu
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 123c9af48d93e23d4f582575848d981f57abd2f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85327885"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Instrukcje: instrumentowanie usługi natywnej i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do instrumentowania natywnej usługi (C/C++) i zbierania szczegółowych danych o chronometrażu.

> [!NOTE]
> Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie może zostać uruchomiona ponownie po uruchomieniu komputera, taka usługa, która jest uruchamiana tylko podczas uruchamiania systemu operacyjnego.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zebrać szczegółowe dane o chronometrażu z usługi natywnej przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika. Następnie należy zamienić nieinstrumentację wersję usługi na wersję instrumentacji, upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Następnie uruchamiasz Profiler.

 Po uruchomieniu usługi dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, Wyłącz usługę, a następnie jawnie wyłącz Profiler.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera

#### <a name="to-start-profiling-a-native-service"></a>Aby rozpocząć profilowanie usługi natywnej

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** , aby wygenerować instrumentację wersji pliku binarnego usługi.

3. Zamień oryginalny plik binarny na wersję z instrumentacją. W Menedżerze sterowania usługami systemu Windows upewnij się, że typ uruchamiania usługi jest ustawiony na ręczny.

4. Uruchom Profiler. Wpisz:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Opcja **/Start: Trace** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (.* VSP*).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Trace** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Określa liczbę sekund oczekiwania na zainicjowanie profilera przed zwróceniem błędu. Jeśli `Interval` nie jest określony, profiler czeka na czas nieokreślony. Domyślnie **/Start** zwraca natychmiast. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w konfiguracji. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |

5. Uruchom usługę z poziomu Menedżera kontroli usług.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, możesz użyć opcji *VSPerfCmd.exe* , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie usługi.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub kończy (**/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku ( `TID` ).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, Zatrzymaj usługę, na której działa składnik instrumentacji, a następnie Wywołaj opcję **VSPerfCmd**[/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zatrzymaj usługę z menedżera kontroli usług.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Zamień moduł z pakietem na oryginalny. W razie potrzeby skonfiguruj ponownie typ uruchomienia usługi.

## <a name="see-also"></a>Zobacz też
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
