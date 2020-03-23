---
title: Dołącz profiler do ASP.NET aplikacji do zbierania danych współbieżności
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 04745140c3f92b3d601a03ddbcd68259b3959364
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776473"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Jak: Dołącz profiler do ASP.NET aplikacji sieci web, aby zbierać dane współbieżności za pomocą wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzi profilowania do dołączania profilera do aplikacji ASP.NET i zbierania danych dotyczących procesu i współbieżności wątku.

Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zebrać dane współbieżności, należy dołączyć profiler do procesu ASP.NET procesu roboczego, który obsługuje witrynę sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty. W większości przypadków należy wyczyścić zmienne środowiskowe profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Załącz profiler

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Aby dołączyć profiler do aplikacji ASP.NET

1. Rozpocznij profiler, wpisując następujące polecenie:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność /dane wyjściowe:** `OutputFile` [`Options`]

   - Opcja [/start](../profiling/start.md) inicjuje profiler do zbierania danych rywalizacji o zasoby.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej opcji w poniższej tabeli z opcją **/start.**

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain\`[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta, któremu ma zostać przyznany dostęp do profilera. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

2. Uruchom aplikację ASP.NET w typowy sposób.

3. Dołącz profiler do procesu ASP.NET procesu roboczego, wpisując następujące polecenie:**VSPerfCmd /attach:** `PID` [**/targetclr:**`Version`]

   - `PID`określa identyfikator lub nazwę procesu ASP.NET pracownika. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Ten parametr jest opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolując zbieranie danych, można zbierać dane dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Pary opcji VSPerfCmd w poniższej tabeli rozpoczyna i zatrzymuje zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu, który określa identyfikator procesu ( ) określa.|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który`PID`określa identyfikator procesu ( ) lub nazwa procesu (*ProcName*). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono żadnego procesu.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z aplikacji, która jest profilowana za pomocą metody współbieżności, uruchamiając ponownie proces ASP.NET procesu roboczego lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana, dopóki komputer nie zostanie ponownie uruchomiony.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd /odłączyć**

2. Zamknij profiler, wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz też
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Szybkie profilowanie witryny sieci Web za pomocą vsperfAspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
