---
title: Dołącz profiler do aplikacji autonomicznej programu .NET Framework; pobierz statystyki aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9084f2d1dd784172735c66d38da785dffb74d82c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779184"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji autonomicznej .NET Framework i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania, aby dołączyć profiler do uruchomionej aplikacji autonomicznej (klienckiej) programu .NET Framework i zebrać statystyki wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.
>
> Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. Zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zebrać dane dotyczące wydajności z aplikacji .NET Framework, należy zainicjować odpowiednie zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji i profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji profilowania.

## <a name="attach-the-profiler"></a>Załącz profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]

   - Opcja **/samplelineoff** wyłącza zbieranie danych numerów wiersza kodu źródłowego.

3. Uruchom profiler. Wpisz:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:sample** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy profilowana aplikacja została uruchomiona jako użytkownik inny niż zalogowany użytkownik. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. **/CS** można określić jako skrót dla **/crosssession**. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

4. W razie potrzeby uruchom aplikację docelową w typowy sposób.

5. Dołącz profiler do aplikacji docelowej. Wpisz:

    **VSPerfCmd /attach:**`PID` {&#124;`ProcessName`}`Sample Event`[ ] [**/targetclr:**`Version`]

   - `PID`określa identyfikator procesu aplikacji docelowej. `ProcessName`określa nazwę procesu. Należy zauważyć, `ProcessName` że jeśli określisz i wiele procesów, które mają taką samą nazwę są uruchomione, wyniki są nieprzewidywalne. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

   - Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 cykli zegara procesora niezatrzymowanych. Jest to około jeden raz na 10 sekund na procesorze 1GH. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania. [/targetclr](../profiling/targetclr.md)**:** `Version` określa wersję clr do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

   |||
   |-|-|
   |Przykładowe zdarzenie|Opis|
   |[/timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę cykli zegara `Interval`niezatrzymowanych, które są określone przez .|
   |[/pf](../profiling/pf.md) [**:**`Interval`]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów strony między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/licznik](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie i interwał próbkowania na licznik `Config`wydajności procesora i interwał, które są określone w .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie `PID`danych dla procesu określonego przez .|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który `PID` jest określony przez nazwę lub proces (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi być odłączony od wszystkich profilowanych procesów i profiler musi być jawnie zamknięty. Profiler można odłączyć od aplikacji, która została sprofilowana przy użyciu metody próbkowania, zamykając aplikację lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Typ **VSPerfCmd /odłączać**

         — lub —

    - Zamknij aplikację docelową.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
