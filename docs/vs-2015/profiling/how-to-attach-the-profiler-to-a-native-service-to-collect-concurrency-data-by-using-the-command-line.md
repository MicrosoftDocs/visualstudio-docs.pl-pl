---
title: 'Instrukcje: Dołącz Profiler do usługi natywnej i zbieranie danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab6e56d6b2d9a953b5549d59ea85049be8cc0306
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432887"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Dołącz Profiler do usługi natywnej i zbieranie danych współbieżności przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do macierzystej (C/C++) usługi i zbierania danych współbieżności procesu i wątku, przy użyciu metody próbkowania.  

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć programu profilującego w wierszu polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH **polecenia** oknie lub do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, Profiler nie może być dołączony do usługi, a Profiler musi być jawnie zamknięty.  

## <a name="attaching-the-profiler"></a>Dołączanie Profiler  
 Aby dołączyć program profilujący do macierzystej usługi, należy użyć **VSPerfCmd/start** i **/ dołączanie** opcje do zainicjowania programu profilującego i dołączenia go do aplikacji docelowej. Można określić **/start** i **/ dołączanie** oraz ich odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych przy uruchamianiu aplikacji docelowej. Następnie użyj **globalon** do rozpoczęcia zbierania danych.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć Profiler do usługi natywnej  

1. Jeśli usługa nie jest uruchomiona, uruchom usługę.  

2. Uruchom program profilujący, wpisując następujące polecenie w wierszu polecenia:  

    [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnej opcji z poniższej tabeli z **/start** opcji.  

   > [!NOTE]
   > Większość usług wymaga **/User** i **/crosssession** opcji.  

   |                               Opcja                               |                                                                     Opis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName` |                           Określa opcjonalną domenę i nazwę użytkownika konta, aby uzyskać dostęp do programu profilującego.                           |
   |           [/crosssession](../profiling/crosssession.md)            |                                               Włącza profilowanie procesów w innych sesjach logowania.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).       |

3. Dołącz profiler do usługi, wpisując następujące polecenie w wierszu polecenia:  

    **Narzędzia VSPerfCmd / dołączania:** `PID`  

    `PID` Określa identyfikator procesu lub nazwę procesu aplikacji docelowej. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą opcji VSPerfCmd.exe. Przez kontrolowanie zbierania danych może zbierać dane dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Pary opcji w poniższej tabeli uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, identyfikator procesu (`PID`) określa.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, identyfikator procesu (`PID`) lub nazwę procesu (*Nazwa_procedury*) określa. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych z macierzystej usługi, która jest profilowana metodą współbieżności, przez zatrzymanie usługi lub wywołując **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Odłącz profiler od aplikacji docelowej, przez zatrzymanie usługi lub wpisując następujące polecenie w wierszu polecenia:  

     Typ **VSPerfCmd / Odłącz**  

2. Zamknij program profilujący, wpisując następujące polecenie w wierszu polecenia:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)
