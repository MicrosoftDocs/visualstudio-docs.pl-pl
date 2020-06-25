---
title: Dołączanie profilera do usługi .NET w celu zbierania danych współbieżności
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 24c49015915b8a1d214a833c38c5550f51c50c13
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328692"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi .NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do usługi .NET Framework i zbierania danych współbieżności procesu i wątku przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane współbieżności, należy dołączyć Profiler do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do usługi, a profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć Profiler do usługi .NET Framework

1. Zainstaluj usługę.

2. Otwórz okno polecenia.

3. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

     [VSPerfCLREnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]

    - **/globalsampleon** włącza próbkowanie.

    - **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Gdy ta opcja jest określona, dane są przypisywane tylko do funkcji.

4. Uruchom ponownie komputer.

5. Uruchom Profiler. Wpisz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency/Output:** `OutputFile` [ `Options` ]

     Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile`Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     W przypadku opcji **/Start** można użyć dowolnej z następujących opcji.

    > [!NOTE]
    > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.

    |Opcja|Opis|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName`|Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows.|
    |[/CrossSession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**.|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*).|

6. W razie potrzeby uruchom usługę.

7. Dołącz profiler do usługi. Wpisz:

     **VSPerfCmd/Attach:** `PID` [[/targetclr](../profiling/targetclr.md)**:** `Version` ]

    - `PID`Określa identyfikator procesu lub nazwę procesu usługi. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    - **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

- Można również użyć opcji/Mark **VSPerfCmd.exe** [/mark](../profiling/mark.md) , aby wstawić znak profilowania do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych. Poniższe pary opcji VSPerfCmd uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych z aplikacji profilowanej przy użyciu metody współbieżności przez zatrzymanie usługi lub wywoływanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej.

    - Zatrzymaj usługę.

         -lub-

    - Wpisz **VSPerfCmd/detach.**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)
