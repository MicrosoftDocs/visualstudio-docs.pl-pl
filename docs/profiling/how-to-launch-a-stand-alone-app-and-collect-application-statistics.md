---
title: 'Wiersz polecenia profilera: Uruchamianie aplikacji autonomicznej, uruchamianie statystyk aplikacji'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fb6228592115091dc538dbe59c227a180e75aa10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775421"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: uruchamianie aplikacji autonomicznej z profilerem i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzi profilowania do uruchamiania aplikacji autonomicznej (klienckiej) i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. Zobacz [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia. Narzędzia profilowania można uruchomić na komputerze, na którym jest zainstalowany program Visual Studio z okna polecenia programu Visual Studio.

1. Jeśli używasz narzędzi profilowania na komputerze, na którym jest zainstalowany program Visual Studio, okno polecenia programu Visual Studio ustawia poprawne ścieżki. W menu **Narzędzia** wybierz polecenie **Vs. wiersz polecenia**

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby uruchomić aplikację docelową przy użyciu profilera, należy użyć vsPerfCmd **/start** i **/launch** opcje zainicjować profiler i uruchomić aplikację. Można określić **/start** i **/launch** oraz ich odpowiednie opcje w jednym wierszu polecenia.

 Można również dodać **/globaloff** opcji wstrzymania zbierania danych na początku aplikacji docelowej. Następnie należy użyć **/globalon,** aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom profiler. Wpisz:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:sample** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   | Opcja | Opis |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

3. Uruchom aplikację docelową. Typ:**VSPerfCmd /launch:** `appName` [`Options`]`Sample Event`

    Z opcją **/launch** można użyć co najmniej jednej z następujących opcji.

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazywane do aplikacji docelowej.|
   |[/konsola](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 cykli zegara procesora niezatrzymowanych. Jest to około jeden raz na 10 sekund na procesorze 1GHz. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę cykli zegara `Interval`niezatrzymowanych, które są określone przez .|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów strony między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/licznik](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie i interwał próbkowania na licznik `Config`wydajności procesora i interwał, które są określone w .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu `PID` określonego przez nazwę lub proces (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może być dołączony do dowolnego procesu profilowanego i profiler musi być jawnie zamknięty. Profiler można odłączyć od aplikacji, która została sprofilowana przy użyciu metody próbkowania, zamykając aplikację lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Zamknij aplikację docelową.

         — lub —

    - Typ **VSPerfCmd /odłączać**

2. Zamknij profiler. Wpisz:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
