---
title: Dołącz profiler do .NET Framework autonomicznej aplikacji; Pobierz statystyki aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 68450129d9bb3e9e67793c0a4155e953abbccc3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531810"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji autonomicznej .NET Framework i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do uruchomionej .NET Framework aplikacji autonomicznej (klient) i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zbierać dane dotyczące wydajności z aplikacji .NET Framework, należy zainicjować odpowiednie zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji profilowania.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv/sampleon** [**/samplelineoff**]

   - Opcja **/samplelineoff** wyłącza zbieranie danych numeru wiersza kodu źródłowego.

3. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: przykład/Output:** `OutputFile` [`Options`]

   - Polecenie [/Start](../profiling/start.md)**: Sample** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć jednej z następujących opcji z opcją **/Start: Sample** .

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa opcjonalną nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy profilowana aplikacja została uruchomiona jako użytkownik inny niż zalogowany użytkownik. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. **/CS** można określić jako skrót dla **/CrossSession**. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |

4. W razie potrzeby Uruchom aplikację docelową w typowy sposób.

5. Dołącz profiler do aplikacji docelowej. Wpisz:

    **VSPerfCmd/Attach:**{ `PID`&#124;`ProcessName` } [ `Sample Event` ] [**/targetclr:** `Version` ]

   - `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

   - Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 10 sekund na procesorze 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania. [/targetclr](../profiling/targetclr.md)**:** `Version` określa wersję środowiska CLR do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

   |Przykładowe zdarzenie|Opis|
   |-|-|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara, które są określone przez `Interval` .|
   |[/PF](../profiling/pf.md) [**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (systemowe). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie próbkowania i interwał na licznik wydajności procesora i interwał, które są określone w `Config` .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określony przez `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. Można odłączyć Profiler od aplikacji, która została profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Wpisz **VSPerfCmd/detach**

         -lub-

    - Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Zobacz też
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
