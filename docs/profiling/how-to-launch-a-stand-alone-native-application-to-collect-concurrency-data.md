---
title: Wiersz polecenia profilera — otwieranie natywnej aplikacji klienckiej, pobieranie danych współbieżności
description: Dowiedz się, jak za pomocą narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania uruchomić natywną autonomiczną aplikację klienta i zebrać dane współbieżności procesu i wątku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: da71c5bb714a50c70cbefcd2a2987a48c14eb4b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928987"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: uruchamianie natywnej aplikacji autonomicznej z profilerem w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do uruchamiania natywnej aplikacji autonomicznej (klienckiej) i zbierania danych współbieżności procesu i wątku.

 Sesja profilowania ma następujące części:

- Uruchamianie aplikacji za pomocą profilera

- Kontrolowanie zbierania danych

- Kończenie sesji profilowania

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby uruchomić aplikację docelową za pomocą profilera, użyj opcji [VSPerfCmd.exe](../profiling/vsperfcmd.md) **/Start** i **przełącznik/Launch** w celu zainicjowania profilera i uruchomienia aplikacji. Można określić **/Start** i **przełącznik/Launch** oraz ich odpowiednie opcje. Możesz również dodać opcję **/GlobalOff** , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. W wierszu polecenia wpisz następujące polecenie:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency/Output:** `OutputFile` [ `Options` ]

     Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z opcji w poniższej tabeli z opcją **/Start: współbieżność** .

    |Opcja|Opis|
    |------------|-----------------|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).|

2. Uruchom aplikację docelową, wpisując:

     **VSPerfCmd**  [przełącznik/Launch](../profiling/launch.md) **:** `AppName` [ `Options` ]

     Można użyć dowolnej z opcji w poniższej tabeli z opcją **przełącznik/Launch** .

    |Opcja|Opis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
    |[/Console](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, jeśli aplikacja ładuje więcej niż jedną wersję środowiska CLR.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z opcjami *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określany przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który określa identyfikator procesu ( `PID` ) lub nazwę procesu (*ProcName*). **/Detach** zatrzyma zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli żaden proces nie zostanie określony.|

- Można również użyć opcji/Mark **VSPerfCmd.exe** [](../profiling/mark.md) , aby wstawić znak profilowania do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych.

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych współbieżności, zamykając profilowaną aplikację lub wywołując opcję **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz Profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd/detach**

2. Zamknij program Profiler, wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)