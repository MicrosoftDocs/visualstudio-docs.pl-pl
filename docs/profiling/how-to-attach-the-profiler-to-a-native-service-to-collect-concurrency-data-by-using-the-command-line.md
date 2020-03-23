---
title: 'VSPerfCmd: Dołącz profiler do usługi macierzystej, aby uzyskać dane współbieżności'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 705e55363f4f8657da20fe66cd4369188f133cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776611"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania, aby dołączyć profiler do natywnej usługi (C/C++) i zbierać dane procesu i współbieżności wątku przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Gdy profiler jest dołączony do usługi, można wstrzymać i wznowić zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do usługi, a profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler"></a>Załącz profiler
 Aby dołączyć profiler do usługi macierzystej, należy użyć **vsPerfCmd/start** i **/attach** opcje zainicjować profiler i dołączyć go do aplikacji docelowej. Można określić **/start** i **/attach** oraz ich odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcji wstrzymania zbierania danych na początku aplikacji docelowej. Następnie należy użyć **/globalon,** aby rozpocząć zbieranie danych.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć profiler do usługi macierzystej

1. Jeśli usługa nie jest uruchomiona, uruchom usługę.

2. Rozpocznij profiler, wpisując w wierszu polecenia następujące elementy:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność /dane wyjściowe:** `OutputFile` [`Options`]

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej opcji w poniższej tabeli z opcją **/start.**

   > [!NOTE]
   > Większość usług wymaga opcji **/user** i **/crosssession.**

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain\`[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta, któremu ma zostać przyznany dostęp do profilera. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |

3. Dołącz profiler do usługi, wpisując następujące polecenie w wierszu polecenia:

    **VSPerfCmd /attach:**`PID`

    `PID`określa identyfikator procesu lub nazwę procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku za pomocą opcji *VSPerfCmd.exe.* Kontrolując zbieranie danych, można zbierać dane dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu, który określa identyfikator procesu ( ) określa.|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który`PID`określa identyfikator procesu ( ) lub nazwa procesu (*ProcName*). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono żadnego procesu.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z usługi macierzystej, która jest profilowana za pomocą metody współbieżności, zatrzymując usługę lub wywołując **vsPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz profiler od aplikacji docelowej, zatrzymując usługę lub wpisując następujące polecenie w wierszu polecenia:

     Typ **VSPerfCmd /odłączać**

2. Zamknij profiler, wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
