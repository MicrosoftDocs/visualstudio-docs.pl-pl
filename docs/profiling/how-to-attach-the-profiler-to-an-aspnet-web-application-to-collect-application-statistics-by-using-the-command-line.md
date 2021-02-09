---
title: Dołącz profiler do ASP.NET, aby uzyskać statystykę aplikacji
description: Użyj narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania, aby dołączyć Profiler do aplikacji sieci Web ASP.NET i uzyskać statystyki wydajności przy użyciu metody próbkowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: acf625bc5762dbc90265ffc81ab0920ea778f010
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887981"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do aplikacji sieci Web ASP.NET i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane dotyczące wydajności z aplikacji sieci Web ASP.NET, należy zainicjować odpowiednie zmienne środowiskowe, a komputer hostujący aplikację sieci Web ASP.NET musi zostać uruchomiony ponownie w celu skonfigurowania serwera sieci Web do profilowania.

 Następnie dołączysz Profiler do procesu roboczego ASP.NET, który hostuje witrynę sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od profilowanej aplikacji, a profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Uruchamianie profilera i dołączanie do aplikacji sieci Web ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć Profiler do aplikacji sieci Web ASP.NET

1. Otwórz okno wiersza polecenia.

2. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** włącza próbkowanie.

   - **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Gdy ta opcja jest określona, dane są przypisywane tylko do funkcji.

3. Uruchom ponownie komputer.

4. Uruchom Profiler. Typ:**VSPerfCmd** [/Start](../profiling/start.md)**: przykład** [/Output](../profiling/output.md)**:** `OutputFile` [ `Options` ]

   - Polecenie **/Start: Sample** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć jednej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl). |

5. Uruchom aplikację sieci Web ASP.NET w typowy sposób.

6. Dołącz profiler do procesu roboczego ASP.NET. Type:**VSPerfCmd** [/Attach](../profiling/attach.md)**:**{ `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]

   - `PID` Określa identyfikator procesu procesu roboczego ASP.NET; `ProcName` określa nazwę procesu roboczego. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 100 razy na sekundę na procesorze 1GH. Możesz określić jedną z następujących opcji **VSPerfCmd** , aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara, które są określone przez `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (systemowe). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie próbkowania i interwał na licznik wydajności procesora i interwał, które są określone w `Config` .|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji.|

   - **targetclr:** `Version` Określa wersję środowiska CLR do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` **/ProcessOff:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określony przez `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez `PID` lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web, a następnie użyj polecenia Internet Information Services (IIS) **IISReset** , aby zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.

 Polecenie **VSPerfCLREnv/GlobalOff** czyści zmienne środowiskowe profilowania. Aby zastosować nowe ustawienia środowiska, należy ponownie uruchomić komputer.

 **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

   - Wpisz **VSPerfCmd/detach**

      -lub-

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy.

2. Zamknij program profilujący. Typ:**VSPerfCmd** [/Shutdown](../profiling/shutdown.md)

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd/globaloff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
