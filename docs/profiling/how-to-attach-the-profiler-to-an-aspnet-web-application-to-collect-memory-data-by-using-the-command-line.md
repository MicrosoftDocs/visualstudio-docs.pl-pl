---
title: Dołączanie profilera do aplikacji ASP.NET w celu zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: edf9fec93b8fed4e89e5e7cf0525d4f11ed326fa
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329345"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym artykule opisano sposób korzystania z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania w celu dołączania profilera do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web i zbierania danych o liczbie i rozmiarze .NET Framework alokacji pamięci. Możesz również zbierać dane dotyczące okresu istnienia .NET Framework obiektów pamięci.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, należy użyć narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) w celu zainicjowania odpowiednich zmiennych środowiskowych na komputerze hostującym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web. Następnie należy ponownie uruchomić komputer, aby skonfigurować serwer sieci Web do profilowania.

 Następnie użyj narzędzia [VSPerfCmd.exe](../profiling/vsperfcmd.md) , aby dołączyć Profiler do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego, który hostuje witrynę sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć Profiler do aplikacji sieci Web ASP.NET

1. Otwórz okno wiersza polecenia.

2. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - Opcje **/globalsamplegc** i **/globalsamplegclife** określają typ danych pamięci do zebrania.

        Określ jedną i tylko jedną z następujących opcji.

       |Opcja|Opis|
       |------------|-----------------|
       |**/globalsamplegc**|Włącza zbieranie danych alokacji pamięci.|
       |**/globalsamplegclife**|Umożliwia zbieranie danych dotyczących danych alokacji pamięci i okresu istnienia obiektu.|

   - Opcja **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Jeśli ta opcja jest określona, dane są przypisywane na poziomie funkcji.

3. Uruchom ponownie komputer, aby ustawić nową konfigurację środowiska.

4. Otwórz okno wiersza polecenia. W razie potrzeby Ustaw zmienną środowiska dla ścieżki profilera.

5. Uruchom Profiler. Wpisz:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: przykład**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Polecenie **/Start: Sample** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile`Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WaitStart](../profiling/waitstart.md) [**:** `Interval` ] | Określa liczbę sekund oczekiwania na zainicjowanie profilera przed zwróceniem błędu. Jeśli `Interval` nie jest określony, profiler czeka na czas nieokreślony. Domyślnie **/Start** zwraca natychmiast. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl). |

6. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web w typowy sposób.

7. Dołącz profiler do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Wpisz:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Identyfikator procesu `(PID)` określa identyfikator procesu lub nazwę procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] roboczego. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - **/targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera przy użyciu opcji **VSPerfCmd.exe** . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez `PID` .|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;: `ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od aplikacji sieci Web. Możesz zatrzymać zbieranie danych z aplikacji, która jest profilowana przy użyciu metody próbkowania przez ponowne uruchomienie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

   - Wpisz **VSPerfCmd** [/Detach](../profiling/detach.md)

      -lub-

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:

     **IISReset/Stop**

2. Zamknij program profilujący. Wpisz:

    **VSPerfCmd/shutdown**

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd/globaloff**

4. Uruchom ponownie komputer. W razie potrzeby uruchom ponownie Internet Information Services (IIS). Wpisz:

    **IISReset/Start**

## <a name="see-also"></a>Zobacz też
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
