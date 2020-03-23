---
title: Dołączanie profilera do aplikacji natywnej i zbieranie danych współbieżności
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 367c91035f5d37bd8b0c20f1df84c7a2ee2d487a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776930"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Jak: Dołączanie profilera do natywnej aplikacji autonomicznej i zbieranie danych współbieżności przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania, aby dołączyć profiler do uruchomionej aplikacji autonomicznej (C/C++) i zbierać dane rywalizacji wątków.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Dołączanie profilera do uruchomionej aplikacji natywnej

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Aby dołączyć profiler do uruchomionej aplikacji natywnej

1. W wierszu polecenia wpisz następujące polecenie:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność**

     Można użyć dowolnej z opcji w poniższej tabeli z **/start:współbieżność** opcji.

    |Opcja|Opis|
    |------------|-----------------|
    |[/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain\`[ ]`Username`|Określa opcjonalną domenę i nazwę użytkownika konta, któremu ma zostać przyznany dostęp do profilera.|
    |[/crosssession](../profiling/crosssession.md)|Umożliwia profilowanie procesów w innych sesjach logowania.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl).|

2. Dołącz profiler do aplikacji docelowej, wpisując następujące polecenie:

     **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{ `ProcName`&#124;}  

     `PID`określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolując zbieranie danych, można zbierać dane dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu, który określa identyfikator procesu ( ) określa.|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który`PID`określa identyfikator procesu ( ) lub nazwa procesu (*ProcName*). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono żadnego procesu.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z aplikacji, która jest profilowana za pomocą metody próbkowania, zamykając aplikację lub wywołując **vsPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie:

     **VSPerfCmd /odłączyć**

2. Zamknij profiler, wpisując następujące polecenie:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
