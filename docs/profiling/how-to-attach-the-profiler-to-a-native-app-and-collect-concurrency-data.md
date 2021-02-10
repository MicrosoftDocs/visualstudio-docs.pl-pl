---
title: Dołączanie profilera do aplikacji natywnej & zbieranie danych współbieżności
description: Użyj narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania, aby dołączyć Profiler do uruchomionej aplikacji autonomicznej (C/C++) i uzyskać dane rywalizacji o wątki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: e1104f17e1932dcdd7c1071d14cb57a01aad8522
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969350"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do natywnej aplikacji autonomicznej i zbieranie danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób korzystania z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania w celu dołączania profilera do uruchomionej aplikacji autonomicznej (C/C++) i zbierania danych rywalizacji o wątki.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Dołącz profiler do uruchomionej aplikacji natywnej

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji natywnej

1. W wierszu polecenia wpisz następujące polecenie:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: współbieżność**

     Można użyć dowolnej z opcji w poniższej tabeli z opcją **/Start: współbieżność** .

    |Opcja|Opis|
    |------------|-----------------|
    |[/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`Username`|Określa opcjonalną nazwę domeny i użytkownika konta, z którym ma zostać udzielony dostęp do profilera.|
    |[/CrossSession](../profiling/crosssession.md)|Umożliwia profilowanie procesów w innych sesjach logowania.|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).|

2. Dołącz profiler do aplikacji docelowej, wpisując następujące polecenie:

     **VSPerfCmd**  [/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` }

     `PID` Określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określany przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który określa identyfikator procesu ( `PID` ) lub nazwę procesu (*ProcName*). **/Detach** zatrzyma zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli żaden proces nie zostanie określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych z aplikacji, która jest profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz Profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie:

     **VSPerfCmd/detach**

2. Zamknij program Profiler, wpisując następujące polecenie:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
