---
title: 'Wiersz polecenia profilera: Instrument dynamiczna ASP.NET aplikacji, pobierz dane chronometrażu'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d8270c9948efe5f9c972f2e4f0eccb035c793953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775460"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Jak: Instrumentowanie dynamicznie skompilowanego ASP.NET aplikacji internetowej i zbieranie szczegółowych danych chronometrażu z profilera za pomocą wiersza polecenia

W tym artykule opisano sposób używania narzędzi wiersza polecenia Visual Studio Profiling Tools do zbierania szczegółowych danych chronometrażu dla dynamicznie skompilowanych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji przy użyciu metody profilowania instrumentacji.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

Aby zbierać dane [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dotyczące wydajności z aplikacji sieci web, należy zmodyfikować plik *web.config* aplikacji docelowej, aby włączyć narzędzie [VSInstr.exe](../profiling/vsinstr.md) do instruowania dynamicznie skompilowanych plików aplikacji. Następnie użyj narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby ustawić odpowiednie zmienne środowiskowe na serwerze sieci web, aby włączyć profilowanie, a następnie ponownie uruchomić komputer.

Uruchom profiler, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Po zakończeniu profilowania zamknij aplikację, zamknij proces roboczy internetowych usług informacyjnych (IIS), a następnie zamknij profiler. Po zakończeniu pracy związanej z profilowania przywróć plik *web.config* i serwer sieci Web do stanu pierwotnego.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie ASP.NET aplikacji sieci Web i serwera sieci web

1. Zmodyfikuj plik *web.config* aplikacji docelowej. Zobacz [Jak: Modyfikowanie plików web.config do instrumentów i profilów dynamicznie skompilowanych ASP.NET aplikacji internetowych](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia.

3. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** umożliwia profilowanie przy użyciu metody instrumentacji.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchamianie sesji profilowania

1. Otwórz okno wiersza polecenia.

2. Uruchom profiler. Wpisz:

     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/start:trace** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację danych profilowania (.* vsp).*

     Można użyć dowolnej z następujących opcji z **/start:trace** opcji.

     > [!NOTE]
     > Opcje **/user** i **/crosssession** są zwykle wymagane dla aplikacji ASP.NET.

     | Opcja | Opis |
     | - | - |
     | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu ASP.NET procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
     | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **Procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z kolekcji danych wstrzymane. Użyj [/globalon,](../profiling/globalon-and-globaloff.md) aby wznowić profilowanie. |
     | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w pliku `Config`. Informacje o liczniku są dodawane do danych, które są zbierane podczas każdego zdarzenia profilowania. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

3. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych`TID`dla wątku określonego przez identyfikator wątku ( ).|

- Można również użyć **vsPerfCmd.exe**[/mark](../profiling/mark.md) opcji wstawić znacznik profilowania do pliku danych. Polecenie **/mark** dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych.

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania

Aby zakończyć sesję profilowania, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zamknij docelową aplikację sieci web, zresetuj usługi IIS, aby zatrzymać profilowany proces, a następnie zamknij profiler.

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, resetując internetowe usługi informacyjne (IIS). Wpisz:

     **IISReset /stop**

3. Zamknij profiler. Wpisz:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

     **Ustawienia IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywracanie konfiguracji aplikacji i komputera

Po zakończeniu profilowania, zastąp plik *web.config,* wyczyść zmienne środowiskowe profilowania i uruchom ponownie komputer, aby przywrócić aplikację i serwer do stanów, w których znajdowały się przed profilowania.

1. Zastąp plik *web.config* kopią oryginalnego pliku.

2. Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też

[Profile ASP.NET widoków](../profiling/command-line-profiling-of-aspnet-web-applications.md)
danych metody[instrumentacji](../profiling/instrumentation-method-data-views.md) aplikacji internetowych
