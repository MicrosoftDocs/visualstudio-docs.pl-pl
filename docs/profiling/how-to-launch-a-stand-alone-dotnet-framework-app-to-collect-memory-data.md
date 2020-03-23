---
title: 'Wiersz polecenia profilera: Otwórz aplikację client .NET Framework, pobierz dane pamięci'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c9ee0ae59fd32394e31acc75184d0e55aaae872d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775361"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Jak: Uruchamianie autonomicznej aplikacji .NET Framework z profilera do zbierania danych pamięci przy użyciu wiersza polecenia
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do uruchamiania aplikacji autonomicznej (klienckiej) programu .NET Framework i zbierania danych pamięci.

 Sesja profilowania ma trzy części:

- Uruchamianie aplikacji przy użyciu profilera.

- Zbieranie danych profilowania.

- Zakończenie sesji profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby uruchomić aplikację docelową przy użyciu profilera, należy użyć **vsPerfCmd.exe.exe/start** i **/launch** opcje zainicjować profiler i uruchomić aplikację. W jednym wierszu polecenia można określić **/start** i **/launch** oraz ich odpowiednie opcje.

 Można również dodać **/globaloff** opcje wstrzymania zbierania danych na początku aplikacji docelowej. Następnie należy użyć **/globalon,** aby rozpocząć zbieranie danych.

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

3. Uruchom aplikację docelową. Wpisz:

    **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `appName` **/gc:**{**alokacja**&#124;okresu **istnienia**}[`Options`]

   - Opcja [/gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` jest wymagana do zbierania danych pamięci .NET Framework. Parametr słowa kluczowego określa, czy mają być zbierane dane alokacji pamięci, czy też zbierać dane alokacji pamięci i okresu istnienia obiektu.

     |Słowo kluczowe|Opis|
     |-------------|-----------------|
     |**Alokacji**|Zbieranie tylko danych alokacji pamięci.|
     |**Okres istnienia**|Zbieranie danych alokacji pamięci i okresu istnienia obiektu.|

     Możesz użyć dowolnej z następujących opcji z opcją **/launch.**

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazywane do aplikacji docelowej.|
   |[/konsola](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
   |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl).|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla`PID`procesu określonego przez identyfikator procesu ( ).|
    |[/attach](../profiling/attach.md) **:** `PID` [/odłączyć](../profiling/detach.md)|**/attach** rozpoczyna zbieranie danych dla procesu, `PID` który jest określony przez (identyfikator procesu). **/detach** zatrzymuje zbieranie danych dla wszystkich procesów.|

- Można również użyć **vsPerfCmd.exe**[/mark](../profiling/mark.md) opcji wstawić znacznik profilowania do pliku danych. Polecenie **/mark** dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą być używane do filtrowania danych.

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi być odłączony od wszystkich profilowanych procesów i profiler musi być jawnie zamknięty. Profiler można odłączyć od aplikacji, która została sprofilowana przy użyciu metody próbkowania, zamykając aplikację lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Zamknij aplikację docelową.

         — lub —

    - Typ **VSPerfCmd /odłączać**

2. Zamknij profiler. Wpisz:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
