---
title: Dołącz profiler do ASP.NET aplikacji internetowej, aby uzyskać statystyki aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 549e43f403b19d8832e00277f826cdc7b276b747
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779080"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Jak: Dołącz profiler do ASP.NET aplikacji sieci web, aby zbierać statystyki aplikacji za pomocą wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do dołączania profilera do aplikacji sieci Web ASP.NET i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. Zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zbierać dane dotyczące wydajności z ASP.NET aplikacji sieci Web, należy zainicjować odpowiednie zmienne środowiskowe i ponownie uruchomić komputer, na którym znajduje się ASP.NET aplikacja sieci Web, aby skonfigurować serwer sieci Web do profilowania.

 Następnie należy dołączyć profiler do procesu roboczego ASP.NET, w którym znajduje się witryna sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi być odłączony od profilowanej aplikacji i profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Uruchamianie profilera i dołączanie do aplikacji sieci web ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć profiler do aplikacji sieci Web ASP.NET

1. Otwórz okno wiersza polecenia.

2. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** umożliwia pobieranie próbek.

   - **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Po określeniu tej opcji dane są przypisywane tylko do funkcji.

3. Uruchom ponownie komputer.

4. Uruchom profiler. Typ:**VSPerfCmd** [/start](../profiling/start.md)**:sample** `Options` [/output](../profiling/output.md)**:**`OutputFile`[ ]

   - Opcja **/start:sample** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu ASP.NET procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |

5. Uruchom ASP.NET aplikacji sieci Web w typowy sposób.

6. Dołącz profiler do procesu ASP.NET procesu roboczego. Typ:**VSPerfCmd** [/attach](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]

   - `PID`określa identyfikator procesu procesu ASP.NET pracownika; `ProcName` określa nazwę procesu roboczego. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 cykli zegara procesora niezatrzymowanych. Jest to około 100 razy na sekundę na procesorze 1GH. Można określić jedną z następujących opcji **VSPerfCmd,** aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę cykli zegara `Interval`niezatrzymowanych, które są określone przez .|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów strony między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)`:``Interval`[ ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/licznik](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie i interwał próbkowania na licznik `Config`wydajności procesora i interwał, które są określone w .|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji.|

   - **targetclr:** `Version` określa wersję clr do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie `PID`danych dla procesu określonego przez .|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu `PID` określonego przez nazwę lub proces (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web, a następnie użyj polecenia **IISReset** internetowych usług informacyjnych (IIS), aby zamknąć proces roboczy. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Wywołanie **vsPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknij plik danych profilowania.

 **Polecenie VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania. Należy ponownie uruchomić komputer, aby można było zastosować nowe ustawienia środowiska.

 Polecenie **VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana, dopóki komputer nie zostanie ponownie uruchomiony.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

   - Typ **VSPerfCmd /odłączać**

      — lub —

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy.

2. Zamknij profiler. Typ:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd /globaloff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
