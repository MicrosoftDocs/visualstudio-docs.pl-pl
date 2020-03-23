---
title: 'Wiersz polecenia profilera: Składnik instrumentów .NET, pobierz dane pamięci'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76d216c4f112f88001b0314a23f22e689f729106
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775904"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Instrukcje: instrumentowanie składnika autonomicznego .NET Framework i zbieranie danych pamięci za pomocą wiersza polecenia profilera
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania do instruowania składnika programu .NET Framework aplikacji autonomicznej, takiej jak plik exe lub dll, i zbierania informacji o pamięci za pomocą profilera.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zebrać dane pamięci ze składnika .NET Framework przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania instrumentalnej wersji składnika i narzędzia [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) do zainicjowania zmiennych środowiskowych profilowania. Następnie należy uruchomić profiler przy użyciu narzędzia *VSPerfCmd.exe.*

 Podczas wykonywania komponentu instrumentowanego dane pamięci są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, należy zamknąć aplikację docelową i jawnie zamknąć profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Narzędzie **VSInstr** służy do generowania instrumentalnej wersji aplikacji docelowej.

3. Inicjowanie zmiennych środowiskowych profilowania programu .NET Framework. Wpisz:

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}

   - Opcje **/tracegc** i **/tracegclife** inicjują zmienne środowiskowe w celu zbierania tylko danych alokacji pamięci lub zbierania danych alokacji pamięci i okresu istnienia obiektu.

       |Opcja|Opis|
       |------------|-----------------|
       |**/tracegc**|Umożliwia zbieranie tylko danych alokacji pamięci.|
       |**/tracegclife**|Umożliwia zbieranie danych alokacji pamięci i okresu istnienia obiektu.|

4. Uruchom profiler. Wpisz:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:trace** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację danych profilowania (.* vsp).*

     Można użyć dowolnej z następujących opcji z **/start:trace** opcji.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie **Procesy** w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **Procesy** Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymaną kolekcją danych, dodaj opcję **/globaloff** do wiersza polecenia **/start.** Użyj **/globalon,** aby wznowić profilowanie. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora, który jest określony w configu. Informacje o liczniku są dodawane do danych, które są zbierane podczas każdego zdarzenia profilowania. |
   | [wydarzenia](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

5. Uruchom aplikację docelową z okna wiersza polecenia.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla`PID`procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla`TID`wątku, który jest określony przez identyfikator wątku ( ).|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, która jest uruchomiona składnik instrumentowany, a następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację docelową.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd /off**

## <a name="see-also"></a>Zobacz też
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
