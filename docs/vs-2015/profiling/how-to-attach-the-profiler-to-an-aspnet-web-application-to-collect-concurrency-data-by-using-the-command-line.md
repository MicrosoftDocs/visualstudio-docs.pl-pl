---
title: 'Instrukcje: Dołącz Profiler do aplikacji sieci Web platformy ASP.NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6340b30f393fc2690a76febf335883b0ebf6f6ed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801766"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Dołącz Profiler do aplikacji sieci Web platformy ASP.NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza polecenia Profiling Tools, aby dołączyć Profiler do aplikacji ASP.NET i zbieranie danych współbieżności procesu i wątku.  

 Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć programu profilującego w wierszu polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH **polecenia** okna lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby zebrać dane współbieżności, profiler musi być dołączony do procesu roboczego ASP.NET, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, Profiler musi nie jest już dołączony do aplikacji, a Profiler musi być jawnie zamknięty. W większości przypadków na końcu sesji należy wyczyścić zmienne środowiskowe profilowania.  

## <a name="attaching-the-profiler"></a>Dołączanie Profiler  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Aby dołączyć Profiler do aplikacji ASP.NET  

1. Rozpocznij program profilujący, wpisując następujące polecenie:  

    [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) opcja inicjuje profiler, aby zbierał dane rywalizacji zasobów.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnej opcji z poniższej tabeli z **/start** opcji.  

   |                               Opcja                               |                                                                     Opis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` |                           Określa opcjonalną domenę i nazwę użytkownika konta, aby uzyskać dostęp do programu profilującego.                           |
   |           [/crosssession](../profiling/crosssession.md)            |                                               Włącza profilowanie procesów w innych sesjach logowania.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).       |


2. Uruchom aplikację ASP.NET w typowy sposób.  

3. Dołącz profiler do procesu roboczego ASP.NET, wpisując następujące polecenie:**VSPerfCmd / dołączanie:** `PID` [**/targetclr:**`Version`]  

   -   `PID` Określa identyfikator lub nazwę procesu roboczego ASP.NET. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   -   [/ targetclr](../profiling/targetclr.md) **:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Ten parametr jest opcjonalny.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą opcji VSPerfCmd.exe. Przez kontrolowanie zbierania danych może zbierać dane dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Pary opcji VSPerfCmd w poniższej tabeli uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, identyfikator procesu (`PID`) określa.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, identyfikator procesu (`PID`) lub nazwę procesu (*Nazwa_procedury*) określa. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych z aplikacji, która jest profilowana metodą współbieżności, poprzez ponowne uruchomienie procesu roboczego ASP.NET lub wywołując **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:  

     **Narzędzia VSPerfCmd / Odłącz**  

2.  Zamknij program profilujący, wpisując następujące polecenie w wierszu polecenia:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Szybkie profilowanie witryny internetowej za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
