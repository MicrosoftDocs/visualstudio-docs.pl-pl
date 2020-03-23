---
title: 'Wiersz polecenia profilera: instrument statyczny ASP.NET aplikacji, pobierz dane pamięci'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98fac9f01219cd398f1d5ec462e3f5165f4638d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775434"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Jak: Instrumentowanie statycznie skompilowanej ASP.NET aplikacji sieci web i zbieranie danych pamięci za pomocą wiersza polecenia profilera
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Narzędzia profilowania do inrządowania wstępnie skompilowanego składnika sieci web lub witryny sieci Web i zbierania alokacji pamięci .NET, okresu istnienia obiektu i szczegółowych danych chronometrażu.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zbierać [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dane ze składnika sieci Web przy użyciu metody instrumentacji, należy użyć narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania instrumentalnej wersji składnika. Na komputerze, na którym znajduje się składnik, można zastąpić nieprzywłosą wersję składnika wersją instrumentamencie. Następnie należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby zainicjować globalne zmienne środowiskowe profilowania i ponownie uruchomić komputer-host. Następnie należy uruchomić profiler.

 Podczas wykonywania komponentu instrumentowanego dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] należy zamknąć proces roboczy, który obsługuje składnik, a następnie jawnie zamknąć profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-to-profile"></a>Zacznij profilować

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Aby przywmiąć składnik sieci Web ASP.NET i rozpocząć profilowanie

1. Narzędzie **VSInstr** służy do generowania instrumentalnej wersji aplikacji docelowej. W razie potrzeby zastąp pliki binarne aplikacji na komputerze ASP.NET hosta na instrumentowane pliki binarne.

2. Otwieranie okna wiersza polecenia

3. Inicjowanie zmiennych środowiskowych profilowania .NET. W oknie wiersza polecenia wpisz:

    **VSPerfClrEnv /globaltracegc**

    — lub —

    **VSPerfClrEnv /globaltracegclife**

   - **/globaltracegc** zbiera dane alokacji pamięci i chronometrażu .NET.

   - **/globaltracegclife** zbiera alokację pamięci .NET, okres istnienia obiektu i szczegółowe dane chronometrażu.

4. Uruchom ponownie komputer.

5. Otwórz okno wiersza polecenia.

6. Uruchom profiler. W oknie wiersza polecenia wpisz:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:trace** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:trace** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta, które jest właścicielem procesu ASP.NET procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik, który jest inny niż zalogowany użytkownik. Nazwa jest wyświetlana w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie **Procesy** Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymaną kolekcją danych, dodaj opcję **/globaloff** do wiersza polecenia **/start.** Użyj **/globalon,** aby wznowić profilowanie. |

7. Otwórz witrynę sieci Web zawierającą komponent instrumentowany.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych`TID`dla wątku określonego przez identyfikator wątku ( ).|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci web, a następnie użyj polecenia **IISReset** internetowych usług informacyjnych (IIS), aby zamknąć proces roboczy. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Wywołanie **vsPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknij plik danych profilowania. **Polecenie VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania. Należy ponownie uruchomić komputer, aby można było zastosować nowe ustawienia środowiska.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:

    **IISReset /stop**

3. Zamknij profiler. Wpisz:

    **VSPerfCmd /shutdown**

4. (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCmd /globaloff**

5. Uruchom ponownie komputer. W razie potrzeby uruchom ponownie usługę IIS. Wpisz:

    **Ustawienia IISReset /start**

## <a name="see-also"></a>Zobacz też
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
