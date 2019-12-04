---
title: 'Wiersz polecenia profilera: składnik .NET klienta instrumentacji, pobieranie danych czasu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ef50983d964c4b7ef6479117ed2501569a77a62d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778911"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Instrukcje: Instrumentacja autonomicznego składnika .NET Framework i zbieranie danych o chronometrażu przy użyciu profilera z wiersza polecenia
W tym temacie opisano, jak używać narzędzi wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania do Instrumentacji składnika .NET Framework, takiego jak. *exe* lub. plik *dll* i zbieranie szczegółowych danych o chronometrażu.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zebrać szczegółowe dane chronometrażu ze składnika .NET Framework przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr. exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika i narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować zmienne środowiskowe profilowania. Następnie uruchamiasz Profiler.

 Gdy składnik Instrumentacji jest wykonywany, dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, zamknij aplikację docelową i jawnie wyłącz Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-profiling-session"></a>Rozpocznij sesję profilowania

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Aby rozpocząć profilowanie przy użyciu metody instrumentacji

1. Otwórz okno wiersza polecenia. W razie potrzeby Dodaj katalog Narzędzia profilera do zmiennej środowiskowej PATH. Ścieżka nie jest dodawana podczas instalacji.

2. Użyj narzędzia **VSInstr** do wygenerowania Instrumentacji wersji aplikacji docelowej.

3. Zainicjuj zmienne środowiskowe profilowania .NET Framework. Wpisz:

    **VSPerfClrEnv/TRACEON**

4. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]

   - Opcja [/Start](../profiling/start.md) **: Trace** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md) **:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć jednej z następujących opcji z opcją **/Start: Trace** .

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z wstrzymanym zbieraniem danych. Aby wznowić profilowanie, użyj [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
   | [/Counter](../profiling/counter.md) **:** `Config` | Zbiera informacje z licznika wydajności procesora określonego w `Config`. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *ETL*). |

5. Uruchom aplikację docelową z okna wiersza polecenia.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera przy użyciu opcji *VSPerfCmd. exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia ( **/GlobalOn**) lub przerywa ( **/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia ( **/ProcessOn**) lub zatrzymywanie ( **/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia ( **/ThreadOn**) lub kończy ( **/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, na której działa składnik Instrumentacji. Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
