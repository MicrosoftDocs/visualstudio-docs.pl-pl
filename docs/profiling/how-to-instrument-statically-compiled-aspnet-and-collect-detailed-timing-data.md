---
title: Wiersz polecenia profilera — statyczna aplikacja ASP.NET, pobieranie danych chronometrażu
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 97d8e18d68ecaf0abf2b3b94e6c22ea6ba3237de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85327922"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Instrukcje: Instrumentacja statycznie skompilowanej aplikacji sieci Web ASP.NET i zbieranie szczegółowych danych o chronometrażu za pomocą profilera przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do instrumentowania prekompilowanego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] składnika sieci Web lub witryny sieci Web i zbierania szczegółowych danych o chronometrażu.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zebrać szczegółowe dane chronometrażu ze [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] składnika sieci Web przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika. Na komputerze, który obsługuje składnik, należy zamienić nieinstrumentację wersji składnika na wersję z instrumentacją. Następnie użyj narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować globalne zmienne środowiskowe profilowania, i uruchom ponownie komputer hosta. Następnie uruchamiasz Profiler.

 Gdy składnik Instrumentacji jest wykonywany, dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, należy zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, który hostuje składnik, a następnie jawnie zamknąć Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-to-profile"></a>Rozpocznij profilowanie

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Aby instrumentować składnik sieci Web ASP.NET i rozpocząć profilowanie

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** do wygenerowania Instrumentacji wersji aplikacji docelowej. W razie potrzeby Zastąp pliki binarne aplikacji na komputerze-hoście ASP.NET przy użyciu plików binarnych instrumentacji.

3. Zainicjuj zmienne środowiskowe profilowania platformy .NET. W oknie wiersza polecenia wpisz:

    **VSPerfClrEnv/globaltraceon**

4. Uruchom ponownie komputer.

5. Otwórz okno wiersza polecenia. W razie potrzeby Ustaw ścieżkę narzędzi profilera.

6. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]

   - Opcja [/Start](../profiling/start.md)**: Trace** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Trace** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** . |

7. Otwórz witrynę sieci Web zawierającą składnik objęty Instrumentacją.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub kończy (**/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku ( `TID` ).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web, a następnie użyj polecenia Internet Information Services (IIS) **IISReset** , aby zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.

 Polecenie **VSPerfCLREnv/GlobalOff** czyści zmienne środowiskowe profilowania. Aby zastosować nowe ustawienia środowiska, należy ponownie uruchomić komputer.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci Web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:

    **IISReset/Stop**

3. Zamknij program profilujący. Wpisz:

    **VSPerfCmd/shutdown**

4. (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd/globaloff**

5. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
