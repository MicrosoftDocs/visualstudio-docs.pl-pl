---
title: Wiersz polecenia profilera — uruchamianie aplikacji autonomicznej, Pobieranie statystyk aplikacji
description: Dowiedz się, jak za pomocą narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania uruchomić autonomiczną aplikację i zebrać dane wydajności przy użyciu metody próbkowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575601f2676a8081422b029d0d7da94b6a4836ca
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883526"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: uruchamianie aplikacji autonomicznej z profilerem i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do uruchamiania autonomicznej aplikacji (klienta) i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędziami profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać je do samego polecenia. Narzędzia profilowania można uruchomić na komputerze, na którym jest zainstalowany program Visual Studio z okna poleceń programu Visual Studio.

1. W przypadku uruchamiania narzędzi profilowania na komputerze, na którym jest zainstalowany program Visual Studio, okno polecenia programu Visual Studio ustawia prawidłowe ścieżki. W menu **Narzędzia** wybierz **wiersz polecenia programu vs**

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby uruchomić aplikację docelową przy użyciu profilera, użyj opcji VSPerfCmd **/Start** i **przełącznik/Launch** , aby zainicjować profiler i uruchomić aplikację. W pojedynczym wierszu polecenia można określić wartości **/Start** i **przełącznik/Launch** oraz ich odpowiednie opcje.

 Możesz również dodać opcję **/GlobalOff** , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: przykład/Output:** `OutputFile` [`Options`]

   - Polecenie [/Start](../profiling/start.md)**: Sample** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   | Opcja | Opis |
   | - | - |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.*ETL*). |

3. Uruchom aplikację docelową. Type:**VSPerfCmd przełącznik/Launch:** `appName` [ `Options` ] [ `Sample Event` ]

    Można użyć co najmniej jednej z następujących opcji z opcją **przełącznik/Launch** .

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
   |[/Console](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 10 sekund na procesorze 1GHz. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara, które są określone przez `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (systemowe). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie próbkowania i interwał na licznik wydajności procesora i interwał, które są określone w `Config` .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**  `PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez `PID` lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może być dołączony do żadnego profilowanego procesu, a profiler musi być jawnie zamknięty. Można odłączyć Profiler od aplikacji, która została profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Zamknij aplikację docelową.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
