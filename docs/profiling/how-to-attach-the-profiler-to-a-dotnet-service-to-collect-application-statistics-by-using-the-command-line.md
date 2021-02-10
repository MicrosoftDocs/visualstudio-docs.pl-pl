---
title: Dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji
description: Użyj programu Visual Studio narzędzia profilowania narzędzia wiersza polecenia, aby dołączyć Profiler do usługi .NET Framework i uzyskać statystyki wydajności przy użyciu metody próbkowania.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 3808f004d9813e846a10c2b672b6406f9cc54cde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958885"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do usługi .NET Framework i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zbierać dane dotyczące wydajności z usługi .NET Framework, należy użyć narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) w celu zainicjowania odpowiednich zmiennych środowiskowych. Następnie należy ponownie uruchomić komputer hostujący usługę i skonfigurować ten komputer do profilowania. Następnie dołączysz Profiler do procesu usługi. Po dołączeniu profilera do usługi można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi i musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć Profiler do usługi .NET Framework

1. Zainstaluj usługę.

2. Otwórz okno wiersza polecenia.

3. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** włącza próbkowanie.

   - **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Gdy ta opcja jest określona, dane są przypisywane tylko do funkcji.

4. Uruchom ponownie komputer.

5. Otwórz okno wiersza polecenia.

6. Uruchom Profiler. Wpisz:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: przykład**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Polecenie **/Start: Sample** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl). |

7. W razie potrzeby uruchom usługę.

8. Dołącz profiler do usługi. Wpisz:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:** { `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Określ identyfikator procesu ( `PID` ) lub nazwę procesu (ProcName) usługi. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

     Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 100 próbek na sekundę w procesorze 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara określonych przez `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (systemowe). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie próbkowania i interwał na licznik wydajności procesora oraz interwał określony w `Config` .|

   - **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, możesz użyć opcji *VSPerfCmd.exe* , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. Można odłączyć od aplikacji profilowanej przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania.

 **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/GlobalOff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
