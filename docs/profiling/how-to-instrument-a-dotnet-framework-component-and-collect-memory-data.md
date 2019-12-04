---
title: 'Wiersz polecenia profilera: składnik .NET klienta instrumentacji, pobieranie danych pamięci'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76d216c4f112f88001b0314a23f22e689f729106
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775904"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Instrukcje: Instrumentacja autonomicznego składnika .NET Framework i zbieranie danych pamięci za pomocą profilera przy użyciu wiersza polecenia
W tym artykule opisano, jak używać narzędzi wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania do Instrumentacji .NET Framework składnika aplikacji autonomicznej, takiej jak plik exe lub dll, i zbierania informacji o pamięci za pomocą profilera.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane pamięci ze składnika .NET Framework przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr. exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika i narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować zmienne środowiskowe profilowania. Następnie uruchamiasz Profiler przy użyciu narzędzia *VSPerfCmd. exe* .

 Po wykonaniu składnika Instrumentacji dane pamięci są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, zamknij aplikację docelową i jawnie wyłącz Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** do wygenerowania Instrumentacji wersji aplikacji docelowej.

3. Zainicjuj zmienne środowiskowe profilowania .NET Framework. Wpisz:

    **VSPerfCLREnv** { **/tracegc** &#124; **/tracegclife**}

   - Opcje **/tracegc** i **/tracegclife** inicjują zmienne środowiskowe, aby zbierać tylko dane alokacji pamięci lub zbierać dane alokacji pamięci i okresu istnienia obiektu.

       |Opcja|Opis|
       |------------|-----------------|
       |**/tracegc**|Włącza zbieranie danych alokacji pamięci.|
       |**/tracegclife**|Włącza zbieranie danych alokacji pamięci i okresu istnienia obiektu.|

4. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]

   - Opcja [/Start](../profiling/start.md) **: Trace** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md) **:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` określa nazwę i lokalizację danych profilowania (. *VSP*).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Trace** .

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** . |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Counter](../profiling/counter.md) **:** `Config` | Zbiera informacje z licznika wydajności procesora określonego w konfiguracji. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [zdarzenia](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *ETL*). |

5. Uruchom aplikację docelową z okna wiersza polecenia.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą opcji *VSPerfCmd. exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn](../profiling/globalon-and-globaloff.md) [/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia ( **/GlobalOn**) lub przerywa ( **/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia ( **/ProcessOn**) lub zatrzymywanie ( **/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia ( **/ThreadOn**) lub przerywa ( **/ThreadOff**) zbieranie danych dla wątku, który jest określony przez identyfikator wątku (`TID`).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, na której działa składnik instrumentacji, a następnie Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd/off**

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
