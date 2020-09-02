---
title: 'Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania danych współbieżności przy użyciu wiersza polecenia | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787656"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi natywnej i zbieranie danych współbieżności przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do natywnej usługi (C/C++) i zbierania danych współbieżności procesu i wątku przy użyciu metody próbkowania.  

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools w katalogu instalacyjnym programu Visual Studio. Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć profilera w wierszu polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna **wiersza polecenia** lub do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do usługi, a profiler musi być jawnie zamknięty.  

## <a name="attaching-the-profiler"></a>Dołączanie profilera  
 Aby dołączyć Profiler do usługi natywnej, należy użyć opcji **VSPerfCmd/Start** i **/Attach** w celu zainicjowania profilera i dołączenia go do aplikacji docelowej. W pojedynczym wierszu polecenia można określić wartości **/Start** i **/Attach** oraz ich odpowiednie opcje. Możesz również dodać opcję **/GlobalOff** , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć Profiler do usługi natywnej  

1. Jeśli usługa nie jest uruchomiona, uruchom usługę.  

2. Uruchom Profiler, wpisując następujące polecenie w wierszu polecenia:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency/Output:** `OutputFile` [ `Options` ]  

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).  

     Można użyć dowolnej opcji w poniższej tabeli z poleceniem **/Start** .  

   > [!NOTE]
   > Większość usług wymaga opcji **/User** i **/CrossSession** .  

   |                               Opcja                               |                                                                     Opis                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` |                           Określa opcjonalną nazwę domeny i użytkownika konta, z którym ma zostać udzielony dostęp do profilera.                           |
   |           [/CrossSession](../profiling/crosssession.md)            |                                               Umożliwia profilowanie procesów w innych sesjach logowania.                                                |
   |  [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`  |                                      Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.                                       |
   |       [/AutoMark](../profiling/automark.md) **:**`Interval`       | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:**`Config`     |       Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).       |

3. Dołącz profiler do usługi, wpisując następujące polecenie w wierszu polecenia:  

    **VSPerfCmd/Attach:**`PID`  

    `PID` Określa identyfikator procesu lub nazwę procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z opcjami VSPerfCmd.exe. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określany przez identyfikator procesu ( `PID` ).|  
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który określa identyfikator procesu ( `PID` ) lub nazwę procesu (*ProcName*). **/Detach** zatrzyma zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli żaden proces nie zostanie określony.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych z natywnej usługi, która jest profilowana przy użyciu metody współbieżności przez zatrzymanie usługi lub wywoływanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Odłącz Profiler od aplikacji docelowej, zatrzymując usługę lub wpisując następujące polecenie w wierszu polecenia:  

     Wpisz **VSPerfCmd/detach**  

2. Zamknij program Profiler, wpisując następujące polecenie w wierszu polecenia:  

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
