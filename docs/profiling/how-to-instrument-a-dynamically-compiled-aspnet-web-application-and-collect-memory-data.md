---
title: 'Wiersz polecenia profilera: Instrument dynamiczna ASP.NET aplikacji, pobierz dane pamięci'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 3378a45ebace942bb8696f2f67962365b5f57796
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778885"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Jak: Instrumentowanie dynamicznie skompilowanej ASP.NET aplikacji sieci web i zbieranie danych pamięci za pomocą wiersza polecenia profilera
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do zbierania [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] szczegółowych danych alokacji pamięci .NET i okresu istnienia obiektu dla dynamicznie skompilowanej aplikacji sieci web przy użyciu metody profilowania instrumentacji.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zbierać dane [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dotyczące wydajności z aplikacji sieci web, należy zmodyfikować plik *web.config* aplikacji docelowej, aby włączyć narzędzie [VSInstr.exe](../profiling/vsinstr.md) do instruowania dynamicznie skompilowanych plików aplikacji. Następnie należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby skonfigurować serwer, na którym znajduje się aplikacja [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web, i włączyć profilowanie pamięci .NET, ustawiając odpowiednie zmienne środowiskowe, a następnie ponownie uruchomić komputer.

 Aby zebrać dane, uruchom profiler, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Po zebraniu odpowiednich danych zamknij aplikację, zamknij proces roboczy internetowych usług informacyjnych (IIS), a następnie zamknij profiler.

 Po zakończeniu pracy związanej z profilowania przywróć plik *web.config* i serwer www do ich pierwotnych stanów.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie ASP.NET aplikacji sieci Web i serwera sieci web

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować ASP.NET aplikacji sieci Web i serwera sieci web

1. Zmodyfikuj plik *web.config* aplikacji docelowej. Zobacz [Jak: Modyfikowanie plików web.config do instrumentów i profilów dynamicznie skompilowanych ASP.NET aplikacji internetowych](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia na komputerze, na którym znajduje się aplikacja internetowa.

3. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

     **VSPerfClrEnv /globaltracegc**

     — lub —

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.

    - **/globaltracegclife** umożliwia zbieranie danych alokacji pamięci i danych okresu istnienia obiektu.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchamianie sesji profilowania

#### <a name="to-profile-the-aspnet-web-application"></a>Aby profilować ASP.NET aplikacji sieci Web

1. Uruchom profiler. Wpisz:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/start:trace** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację danych profilowania (.* vsp).*

     Można użyć dowolnej z następujących opcji z **/start:trace** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] konta, które jest właścicielem procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Nazwa jest wyświetlana w kolumnie **Nazwa użytkownika** na karcie **Procesy** w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **Procesy** Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z kolekcji danych wstrzymane. Użyj [/globalon,](../profiling/globalon-and-globaloff.md) aby wznowić profilowanie. |
   | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności `Config`procesora określonego w pliku . Informacje o liczniku są dodawane do danych zebranych podczas każdego zdarzenia profilowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

2. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku danych profilera przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych`TID`dla wątku określonego przez identyfikator wątku ( ).|

- Można również użyć **vsPerfCmd.exe**[/mark](../profiling/mark.md) opcji wstawić znacznik profilowania do pliku danych. Polecenie **/mark** dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych.

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zamknij docelową aplikację sieci web, zatrzymaj internetowe usługi informacyjne (IIS), aby zatrzymać profilowany proces, a następnie zamknij profiler. Następnie uruchom ponownie usługę IIS.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, resetując internetowe usługi informacyjne (IIS). Wpisz:

    **IISReset /stop**

3. Zamknij profiler. Wpisz:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

    **Ustawienia IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywracanie konfiguracji aplikacji i komputera
 Po zakończeniu profilowania zastąp plik *web.config,* wyczyść zmienne środowiskowe profilowania [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i uruchom ponownie komputer, aby przywrócić serwer i aplikację do ich oryginalnych stanów.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera

1. Zastąp plik *web.config* kopią oryginalnego pliku.

2. (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
