---
title: 'Wiersz polecenia profilera: Komponent natywny instrument, uzyskaj dane chronometrażu'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: fc7bb0a5e853edee4ff28cded94a5d576a13b596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775447"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Jak: Instrumentowanie natywnego komponentu autonomicznego i zbieranie danych chronometrażu za pomocą profilera z wiersza polecenia
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do instruowania składnika macierzystego, takiego jak C++. *exe* lub . *dll* i do zbierania szczegółowych danych chronometrażu.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

Aby zebrać szczegółowe dane chronometrażu ze składnika przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania instrumentalnej wersji składnika. Następnie należy uruchomić profiler. Podczas wykonywania komponentu instrumentowanego dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, należy zamknąć aplikację docelową, a następnie jawnie zamknąć profiler.

## <a name="start-the-profiling-session"></a>Rozpoczynanie sesji profilowania

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Aby rozpocząć profilowanie przy użyciu metody instrumentacji

1. Otwórz okno wiersza polecenia.

2. Narzędzie **VSInstr** służy do generowania instrumentalnej wersji aplikacji docelowej.

3. Uruchom profiler. Wpisz:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:trace** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć jednej lub więcej z następujących opcji z **/start:trace** opcji.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z kolekcji danych wstrzymane. Użyj [/globalon,](../profiling/globalon-and-globaloff.md) aby wznowić profilowanie. |
   | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w pliku `Config`. Informacje o liczniku są dodawane do danych, które są zbierane podczas każdego zdarzenia profilowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

4. Uruchom aplikację docelową w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla`PID`procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla`TID`wątku, który jest określony przez identyfikator wątku ( ).|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, która jest uruchomiona składnik instrumentowany, a następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację docelową.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
