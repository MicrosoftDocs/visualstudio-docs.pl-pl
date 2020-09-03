---
title: 'Instrukcje: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d720779019ab4106fa6c4b727e9994f168a2d8f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179279"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji internetowej ASP.NET w celu zbierania danych współbieżności użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do aplikacji ASP.NET i zbierania danych współbieżności procesu i wątku.  

 Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools w katalogu instalacyjnym programu Visual Studio. Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć profilera w wierszu polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna **wiersza polecenia** lub dodać do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby zbierać dane współbieżności, należy dołączyć Profiler do procesu roboczego ASP.NET, który hostuje witrynę sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty. W większości przypadków należy wyczyścić zmienne środowiskowe profilowania na końcu sesji.  

## <a name="attaching-the-profiler"></a>Dołączanie profilera  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Aby dołączyć Profiler do aplikacji ASP.NET  

1. Uruchom Profiler, wpisując następujące polecenie:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency/Output:** `OutputFile` [ `Options` ]  

   - Opcja [/Start](../profiling/start.md) inicjuje profiler, aby zbierać dane rywalizacji o zasoby.  

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).  

     Można użyć dowolnej opcji w poniższej tabeli z poleceniem **/Start** .  

   |                               Opcja                               |                                                                     Opis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` |                           Określa opcjonalną nazwę domeny i użytkownika konta, z którym ma zostać udzielony dostęp do profilera.                           |
   |           [/CrossSession](../profiling/crosssession.md)            |                                               Umożliwia profilowanie procesów w innych sesjach logowania.                                                |
   |  [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`  |                                      Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.                                       |
   |       [/AutoMark](../profiling/automark.md) **:**`Interval`       | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:**`Config`     |       Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).       |

2. Uruchom aplikację ASP.NET w typowy sposób.  

3. Dołącz profiler do procesu roboczego ASP.NET, wpisując następujące polecenie:**VSPerfCmd/Attach:** `PID` [**/targetclr:** `Version` ]  

   - `PID` Określa identyfikator lub nazwę procesu roboczego ASP.NET. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  

   - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Ten parametr jest opcjonalny.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji VSPerfCmd.exe. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Pary opcji VSPerfCmd w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [ProcessOff](../profiling/processon-and-processoff.md) **:**  `PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określany przez identyfikator procesu ( `PID` ).|  
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który określa identyfikator procesu ( `PID` ) lub nazwę procesu (*ProcName*). **/Detach** zatrzyma zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli żaden proces nie zostanie określony.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z aplikacji profilowanej przy użyciu metody współbieżności przez ponowne uruchomienie procesu roboczego ASP.NET lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Odłącz Profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:  

     **VSPerfCmd/detach**  

2. Zamknij program Profiler, wpisując następujące polecenie w wierszu polecenia:  

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
