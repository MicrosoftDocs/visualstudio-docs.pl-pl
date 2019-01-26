---
title: Dołączanie profilera do usługi .NET w celu zbierania danych współbieżności
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e0756f3c420b759ee47e685005a94b4396a9e143
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019401"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Dołączanie profilera do usługi .NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi i zbierania danych współbieżności procesu i wątku, przy użyciu metody próbkowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.  

 Aby zebrać dane współbieżności, profiler musi być dołączony do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler musi nie jest już dołączony do usługi, a następnie program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  
  
## <a name="attach-the-profiler"></a>Dołącz profiler  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć profiler do usługi .NET Framework  
  
1.  Zainstaluj usługę.  
  
2.  Otwórz okno poleceń.  
  
3.  Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  
  
     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** umożliwia pobieranie próbek.  
  
    -   **/samplelineoff** wyłącza przypisanie zebranych danych do określonego źródła wierszy kodu. Gdy ta opcja jest określona, dane są przypisane tylko do funkcji.  
  
4.  Uruchom ponownie komputer.  
  
5.  Uruchom program profiler. Wpisz:  
  
     [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  
  
     Można użyć dowolnego z następujących opcji z **/start** opcji.  
  
    > [!NOTE]
    >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla usług.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Sesja identyfikator jest wymieniony w **identyfikator sesji** kolumny na **procesy** kartę w Menedżerze zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności Windows mają być zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku.|  
  
6.  Jeśli to konieczne, uruchom usługę.  
  
7.  Dołącz profiler do usługi. Wpisz:  
  
     **Narzędzia VSPerfCmd / dołączanie:** `PID` [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   `PID` Określa identyfikator procesu lub nazwę procesu usługi. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  
  
    -   **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy usługa jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |**/ Dołączanie:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ Dołączanie** rozpoczyna się zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
-   Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych. Następujące pary opcji VSPerfCmd uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych z aplikacji profilowanej metodą współbieżności przez zatrzymanie usługi lub wywołanie **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć program profiler od aplikacji docelowej.  
  
    -   Zatrzymaj usługę.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / Odłącz.**  
  
2.  Zamknij program profilujący. Wpisz:  
  
     **Narzędzia VSPerfCmd**[zamknięcia](../profiling/shutdown.md)
