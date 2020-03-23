---
title: Dołączanie profilera do aplikacji ASP.NET do zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: f2b9ea7799656b0dd7dacd35bde62dc84aea08dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779067"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Jak: Dołącz profiler do ASP.NET aplikacji sieci web do zbierania danych pamięci za pomocą wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Narzędzia profilowania do dołączania profilera do aplikacji sieci Web i zbierania danych dotyczących liczby i rozmiaru alokacji pamięci programu .NET Framework. Można również zbierać dane dotyczące okresu istnienia obiektów pamięci programu .NET Framework.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zebrać dane [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dotyczące wydajności z aplikacji sieci Web, należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aby zainicjować odpowiednie zmienne środowiskowe na komputerze, na którym znajduje się aplikacja sieci Web. Następnie należy ponownie uruchomić komputer, aby skonfigurować serwer sieci Web do profilowania.

 Następnie użyj narzędzia [VSPerfCmd.exe,](../profiling/vsperfcmd.md) aby dołączyć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profiler do procesu roboczego, który obsługuje witrynę sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji i profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Załącz profiler

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć profiler do aplikacji sieci web ASP.NET

1. Otwórz okno wiersza polecenia.

2. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - Opcje **/globalsamplegc** i **/globalsamplegclife** określają typ danych pamięci do zbierania.

        Określ jedną i tylko jedną z następujących opcji.

       |Opcja|Opis|
       |------------|-----------------|
       |**/globalsamplegc**|Umożliwia zbieranie danych alokacji pamięci.|
       |**/globalsamplegclife**|Umożliwia zbieranie danych alokacji pamięci i danych okresu istnienia obiektu.|

   - Opcja **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Jeśli ta opcja jest określona, dane są przypisywane na poziomie funkcji.

3. Uruchom ponownie komputer, aby ustawić nową konfigurację środowiska.

4. Otwórz okno wiersza polecenia. W razie potrzeby ustaw zmienną środowiska ścieżki profilera.

5. Uruchom profiler. Wpisz:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/start:sample** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu ASP.NET procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przez profiler, zanim zwróci błąd. Jeśli `Interval` nie zostanie określony, profiler czeka przez czas nieokreślony. Domyślnie **/start** zwraca natychmiast. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |

6. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web w typowy sposób.

7. Dołącz profiler do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Wpisz:

    **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{ `ProcName`&#124;} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Identyfikator procesu `(PID)` określa identyfikator procesu lub nazwę procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] roboczego. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - **/targetclr:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku danych profilera przy użyciu opcji **VSPerfCmd.exe.** Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) `PID`zbieranie danych dla procesu określonego przez .|
    |**/attach:**`PID` {&#124;`ProcName`} [/detach](../profiling/detach.md)[`PID` **:**{`ProcName`&#124;: }]|**/attach** rozpoczyna zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi być odłączony od aplikacji sieci Web. Można zatrzymać zbieranie danych z aplikacji, która jest profilowana za [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pomocą metody próbkowania, uruchamiając ponownie proces roboczy lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana, dopóki komputer nie zostanie ponownie uruchomiony.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

   - Typ **VSPerfCmd** [/odłączać](../profiling/detach.md)

      — lub —

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:

     **IISReset /stop**

2. Zamknij profiler. Wpisz:

    **VSPerfCmd /shutdown**

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd /globaloff**

4. Uruchom ponownie komputer. W razie potrzeby uruchom ponownie internetowe usługi informacyjne (IIS). Wpisz:

    **Ustawienia IISReset /start**

## <a name="see-also"></a>Zobacz też
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
