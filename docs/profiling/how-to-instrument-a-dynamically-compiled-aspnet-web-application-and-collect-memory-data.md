---
title: 'Instrukcje: Instrumentacja aplikacji sieci web dynamicznie kompilowany ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 172f4a367aa520ebd0fac62d25007713c47e5801
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386274"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Instrukcje: Instrument dynamicznie skompilowanej aplikacji sieci web ASP.NET i pamięci zbierania danych przy użyciu wiersza polecenia profilera
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza poleceń Profiling Tools do zbierania szczegółowych danych pamięci .NET alokacji i obiekt okresu istnienia dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web przy użyciu Instrumentacji, metoda profilowania.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, możesz zmodyfikować *web.config* pliku aplikacji docelowej, aby umożliwić [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej pliki aplikacji. Następnie użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie w celu skonfigurowania serwera, który jest hostem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web i Włączanie profilowania pamięci środowiska .NET, ustawiając odpowiednie zmienne środowiskowe i uruchom ponownie komputer.

 Aby zebrać dane, uruchom program profilujący, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Po zebraniu odpowiednich danych, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie zamknij program profilujący.

 Po zakończeniu profilowania pracy przywracania *web.config* plików i serwera sieci web do ich oryginalnej stanów.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie serwera sieci web i aplikacji sieci web platformy ASP.NET

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować serwer sieci web i aplikacji sieci web platformy ASP.NET

1. Modyfikowanie *web.config* pliku aplikacji docelowej. Zobacz [jak: Modyfikowanie plików web.config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia na komputerze, który jest hostem aplikacji sieci web.

3. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaltracegc**

     —lub—

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.

    - **/globaltracegclife** umożliwia zbieranie danych alokacji pamięci i danych o okresie istnienia obiektu.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchom sesję profilowania

#### <a name="to-profile-the-aspnet-web-application"></a>Aby przeprowadzić profilowanie aplikacji sieci web ASP.NET

1. Uruchom program profiler. Wpisz:

    **Narzędzia VSPerfCmd** [/start](../profiling/start.md) **: śledzenia** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **Polecenia** opcja inicjuje profiler.

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.

   > [!NOTE]
   > **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa opcjonalny nazwę domeny i użytkownika konta, które jest właścicielem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Nazwa jest wyświetlana w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Sesja identyfikator jest wymieniony w **identyfikator sesji** kolumny na **procesy** kartę w Menedżerze zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Rozpoczyna się, które wstrzymana profilera ze zbieraniem danych. Użyj [globalon](../profiling/globalon-and-globaloff.md) Aby wznowić profilowanie. |
   | [/ Licznik](../profiling/counter.md) **:** `Config` | Zbiera informacje z wydajności procesora, licznik określone w `Config`. Informacje licznika są dodawane do danych zbieranych podczas każdego zdarzenia profilowania. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |

2. Rozpocznij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|

- Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny tekst zdefiniowany przez użytkownika ciągu. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania
 Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, Zatrzymaj Internet Information Services (IIS) do Zatrzymaj PROFILOWANEGO procesu, a następnie zamknij program profilujący. Następnie uruchom ponownie usługi IIS.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego poprzez zresetowanie Internet Information Services (IIS). Wpisz:

    **Polecenie IISReset/Stop**

3. Zamknij program profilujący. Wpisz:

    **Narzędzia VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

    **Polecenie IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywróć konfigurację aplikacji i komputera
 Po ukończeniu wszystkich zadań profilowania, Zastąp *web.config* pliku, wyczyść zmienne środowiskowe profilowania i ponownie uruchom komputer, aby przywrócić serwer i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji do ich oryginalnej stanów.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera

1. Zastąp *web.config* plik z kopią oryginalnego pliku.

2. (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **Narzędzia VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
