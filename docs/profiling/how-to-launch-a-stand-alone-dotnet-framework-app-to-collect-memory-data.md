---
title: Wiersz polecenia profilera — Otwieranie aplikacji .NET Framework klienta, pobieranie danych pamięci
description: Dowiedz się, jak używać narzędzi wiersza polecenia narzędzia profilowania Visual Studio do uruchamiania .NET Framework aplikacji autonomicznej i zbierania danych dotyczących aktywności pamięci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a0df21a4d34d3d3f889442046b594ff63f01bcb6
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883488"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: uruchamianie autonomicznej aplikacji .NET Framework z profilerem w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do uruchamiania .NET Framework autonomicznej aplikacji (klienta) i zbierania danych pamięci.

 Sesja profilowania ma trzy części:

- Uruchamianie aplikacji przy użyciu profilera.

- Zbieranie danych profilowania.

- Kończenie sesji profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby uruchomić aplikację docelową przy użyciu profilera, użyj opcji **VSPerfCmd.exe/Start** i **przełącznik/Launch** w celu zainicjowania profilera i uruchomienia aplikacji. W jednym wierszu polecenia można określić **/Start** i **przełącznik/Launch** oraz ich odpowiednie opcje.

 Możesz również dodać opcje **/GlobalOff** , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: przykład/Output:** `OutputFile` [`Options`]

   - Polecenie [/Start](../profiling/start.md)**: Sample** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   | Opcja | Opis |
   | - | - |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |

3. Uruchom aplikację docelową. Wpisz:

    **VSPerfCmd**  [przełącznik/Launch](../profiling/launch.md) **:** `appName` **/GC:**{**Allocation**&#124;**Lifetime**} [ `Options` ]

   - Opcja [/GC](../profiling/gc-vsperfcmd.md)**:** `Keyword` jest wymagana do zbierania danych pamięci .NET Framework. Parametr słowo kluczowe Określa, czy zbierać dane alokacji pamięci, czy zbierać dane alokacji pamięci i okresu istnienia obiektu.

     |Słowo kluczowe|Opis|
     |-------------|-----------------|
     |**Dział**|Zbieraj tylko dane alokacji pamięci.|
     |**okres istnienia**|Zbieraj dane alokacji pamięci i okresu istnienia obiektu.|

     W przypadku opcji **przełącznik/Launch** można użyć dowolnej z następujących opcji.

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
   |[/Console](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
   |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:** `PID` [/Detach](../profiling/detach.md)|**/Attach** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` (identyfikator procesu). **/Detach** zatrzyma zbieranie danych dla wszystkich procesów.|

- Można również użyć opcji/Mark **VSPerfCmd.exe** [](../profiling/mark.md) , aby wstawić znak profilowania do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych.

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. Można odłączyć Profiler od aplikacji, która została profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Zamknij aplikację docelową.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
