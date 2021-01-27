---
title: Wiersz polecenia profilera — składnik natywny instrumentacji, pobieranie danych chronometrażu
description: Dowiedz się, jak za pomocą narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania zbierać szczegółowe dane o chronometrażu dla składnika natywnego, takiego jak plik C++. exe lub. dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 0f9deae5372b6fdc22728fbf7df0c678ffb39c45
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883582"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Instrukcje: Instrumentacja natywnego składnika autonomicznego i zbieranie danych o chronometrażu przy użyciu profilera z wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do Instrumentacji składnika macierzystego, takiego jak C++.*exe* lub. plik *dll* i zbieranie szczegółowych danych o chronometrażu.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

Aby zebrać szczegółowe dane chronometrażu z składnika przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika. Następnie uruchamiasz Profiler. Gdy składnik Instrumentacji jest wykonywany, dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, zamknij aplikację docelową, a następnie jawnie Zamknij Profiler.

## <a name="start-the-profiling-session"></a>Rozpocznij sesję profilowania

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Aby rozpocząć profilowanie przy użyciu metody instrumentacji

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** do wygenerowania Instrumentacji wersji aplikacji docelowej.

3. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]

   - Opcja [/Start](../profiling/start.md)**: Trace** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć co najmniej jednej z następujących opcji z opcją **/Start: Trace** .

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z wstrzymanym zbieraniem danych. Aby wznowić profilowanie, użyj [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w `Config` . Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.*ETL*). |

4. Uruchom aplikację docelową w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub przerywa (**/ThreadOff**) zbieranie danych dla wątku, który jest określony przez identyfikator wątku ( `TID` ).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, na której działa składnik instrumentacji, a następnie Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Zobacz także
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
