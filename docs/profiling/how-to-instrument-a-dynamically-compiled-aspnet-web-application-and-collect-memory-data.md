---
title: 'Wiersz polecenia profilera: Instrumentacja dynamiczna ASP.NET aplikacji, pobieranie danych pamięci'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778885"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji sieci Web ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym temacie opisano, jak za pomocą narzędzia wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania zbierać szczegółowe dane alokacji pamięci .NET i czas istnienia obiektu dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu metody profilowania Instrumentacji.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, należy zmodyfikować plik *Web. config* aplikacji docelowej, aby umożliwić narzędziu [VSInstr. exe](../profiling/vsinstr.md) instrumentację dynamicznie skompilowanych plików aplikacji. Następnie użyj narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby skonfigurować serwer hostujący aplikację sieci Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i włączyć Profilowanie pamięci platformy .NET przez ustawienie odpowiednich zmiennych środowiskowych, a następnie ponownie uruchom komputer.

 Aby zebrać dane, uruchom Profiler, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Po zebraniu odpowiednich danych Zamknij aplikację, Zamknij proces roboczy Internet Information Services (IIS), a następnie wyłącz Profiler.

 Po ukończeniu pracy profilowania, Przywróć oryginalne Stany pliku *Web. config* i serwera sieci Web.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie aplikacji sieci Web ASP.NET i serwera sieci Web

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować aplikację sieci Web ASP.NET i serwer sieci Web

1. Zmodyfikuj plik *Web. config* aplikacji docelowej. Zobacz [jak: Modyfikowanie plików Web. config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia na komputerze hostującym aplikację sieci Web.

3. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/globaltracegc**

     lub

     **VSPerfClrEnv/globaltracegclife**

    - **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.

    - **/globaltracegclife** umożliwia zbieranie danych przydziału pamięci i danych o okresie istnienia obiektu.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchamianie sesji profilowania

#### <a name="to-profile-the-aspnet-web-application"></a>Aby profilować aplikację sieci Web ASP.NET

1. Uruchom Profiler. Wpisz:

    **VSPerfCmd** [/Start](../profiling/start.md) **: Trace** [/Output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/Start: Trace** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` określa nazwę i lokalizację danych profilowania (. *VSP*).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Trace** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Określa opcjonalną nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Nazwa jest wyświetlana w kolumnie **Nazwa użytkownika** na karcie **procesy** w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Uruchamia profiler z wstrzymanym zbieraniem danych. Aby wznowić profilowanie, użyj [/GlobalOn](../profiling/globalon-and-globaloff.md) . |
   | [/Counter](../profiling/counter.md) **:** `Config` | Zbiera informacje z licznika wydajności procesora określonego w `Config`. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [/WinCounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:** `Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *ETL*). |

2. Uruchom aplikację sieci Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera przy użyciu opcji *VSPerfCmd. exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia ( **/GlobalOn**) lub przerywa ( **/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia ( **/ProcessOn**) lub zatrzymywanie ( **/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia ( **/ThreadOn**) lub kończy ( **/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|

- Można również użyć opcji **VSPerfCmd. exe**[/Mark](../profiling/mark.md) , aby wstawić znak profilowania do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych.

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację docelową [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], Zatrzymaj Internet Information Services (IIS), aby zatrzymać profilowany proces, a następnie wyłącz Profiler. Następnie uruchom ponownie usługi IIS.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij aplikację sieci Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Zamknij proces roboczy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] przez zresetowanie Internet Information Services (IIS). Wpisz:

    **IISReset/Stop**

3. Zamknij program profilujący. Wpisz:

    **VSPerfCmd** [/Shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

    **IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywracanie konfiguracji aplikacji i komputera
 Po ukończeniu wszystkich profilowania Zastąp plik *Web. config* , wyczyść zmienne środowiskowe profilowania i uruchom ponownie komputer, aby przywrócić oryginalne Stany serwera programu i aplikacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera

1. Zastąp plik *Web. config* kopią oryginalnego pliku.

2. (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd/globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
