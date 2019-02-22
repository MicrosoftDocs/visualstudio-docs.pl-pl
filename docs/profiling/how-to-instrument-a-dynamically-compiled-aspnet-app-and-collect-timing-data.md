---
title: 'Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET Web i zbieranie danych o chronometrażu przy użyciu Profiler przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: ae33644c72288f79d6be9fcc1aec476939980a5c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646164"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Instrukcje: Instrument dynamicznie skompilowanej aplikacji sieci web ASP.NET i zbieranie szczegółowych danych o chronometrażu przy użyciu profilera przy użyciu wiersza polecenia

W tym artykule opisano, jak używać narzędzi wiersza polecenia programu Visual Studio Profiling Tools do zbierania danych o chronometrażu dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikację za pomocą metoda profilowania instrumentacji.

> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, możesz zmodyfikować *web.config* pliku aplikacji docelowej, aby umożliwić [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej pliki aplikacji. Następnie użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby ustawić odpowiednie zmienne środowiskowe na serwerze sieci web, aby włączyć profilowanie, a następnie uruchom ponownie komputer.

Uruchom program profilujący, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Po zakończeniu profilowania, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie zamknij program profilujący. Po zakończeniu profilowania pracy przywracania *web.config* plików i serwera sieci Web do ich oryginalnej stanów.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie serwera sieci web i aplikacji sieci web platformy ASP.NET

1. Modyfikowanie *web.config* pliku aplikacji docelowej. Zobacz [jak: Modyfikowanie plików web.config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia.

3. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** Włącza profilowanie przy użyciu metody instrumentacji.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchom sesję profilowania

1. Otwórz okno wiersza polecenia.

2. Uruchom program profiler. Wpisz:

     **Narzędzia VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **Polecenia** opcja inicjuje profiler.

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.

     > [!NOTE]
     > **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.

     | Opcja | Opis |
     | - | - |
     | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows. |
     | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w **identyfikator sesji** kolumny na **procesy** kartę w Menedżerze zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Rozpoczyna się, które wstrzymana profilera ze zbieraniem danych. Użyj [globalon](../profiling/globalon-and-globaloff.md) Aby wznowić profilowanie. |
     | [/ Licznik](../profiling/counter.md) **:** `Config` | Zbiera informacje licznika wydajności procesora, który jest określony w `Config`. Informacje o liczniku jest dodawany do danych, które są zbierane podczas każdego zdarzenia profilowania. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
     | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |


3. Rozpocznij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

- Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|

- Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, Zresetuj usługi IIS, aby zatrzymać PROFILOWANEGO procesu, a następnie zamknij program profilujący.

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego poprzez zresetowanie Internet Information Services (IIS). Wpisz:

     **Polecenie IISReset/Stop**

3. Zamknij program profilujący. Wpisz:

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

     **Polecenie IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywróć konfigurację aplikacji i komputera

Po ukończeniu wszystkich zadań profilowania, Zastąp *web.config* pliku, wyczyść zmienne środowiskowe profilowania i ponowne uruchomienie komputera, aby przywrócić stanów, które znajdowały się przed rozpoczęciem profilowania aplikacji i serwera.

1. Zastąp *web.config* plik z kopią oryginalnego pliku.

2. Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **Narzędzia VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także

[Profil aplikacji sieci web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
[widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)