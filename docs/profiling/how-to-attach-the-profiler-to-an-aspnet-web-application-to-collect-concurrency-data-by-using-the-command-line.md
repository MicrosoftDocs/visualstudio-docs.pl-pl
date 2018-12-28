---
title: Dołącz profiler do aplikacji platformy ASP.NET do zbierania danych cncurrency
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: edc3971841bffab19e49ba5e884a157fe4233b0a
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592758"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Dołącz profiler do aplikacji sieci web ASP.NET do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do aplikacji ASP.NET i zbieranie danych współbieżności procesu i wątku.  

Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.  
  
 Aby zebrać dane współbieżności, profiler musi być dołączony do procesu roboczego ASP.NET, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler musi nie jest już dołączony do aplikacji, a Profiler musi być jawnie zamknięty. W większości przypadków na końcu sesji należy wyczyścić zmienne środowiskowe profilowania.  

## <a name="attach-the-profiler"></a>Dołącz profiler  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Aby dołączyć profiler do aplikacji ASP.NET  

1. Rozpocznij program profilujący, wpisując następujące polecenie:  

    [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md) opcja inicjuje profiler, aby zbierał dane rywalizacji zasobów.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnej opcji z poniższej tabeli z **/start** opcji.  

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta, aby uzyskać dostęp do programu profilującego. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |


2. Uruchom aplikację ASP.NET w typowy sposób.  

3. Dołącz profiler do procesu roboczego ASP.NET, wpisując następujące polecenie:**VSPerfCmd / dołączanie:** `PID` [**/targetclr:**`Version`]  

   -   `PID` Określa identyfikator lub nazwę procesu roboczego ASP.NET. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   -   [/ targetclr](../profiling/targetclr.md) **:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Ten parametr jest opcjonalny.  

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą *VSPerfCmd.exe* opcje. Przez kontrolowanie zbierania danych może zbierać dane dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Pary opcji VSPerfCmd w poniższej tabeli uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, identyfikator procesu (`PID`) określa.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, identyfikator procesu (`PID`) lub nazwę procesu (*Nazwa_procedury*) określa. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych z aplikacji, która jest profilowana metodą współbieżności, poprzez ponowne uruchomienie procesu roboczego ASP.NET lub wywołując **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:  

     **Narzędzia VSPerfCmd / Odłącz**  

2.  Zamknij program profilujący, wpisując następujące polecenie w wierszu polecenia:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Zobacz także  
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Szybkie profilowanie za pomocą polecenia VSPerfASPNETCmd witryny sieci web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)