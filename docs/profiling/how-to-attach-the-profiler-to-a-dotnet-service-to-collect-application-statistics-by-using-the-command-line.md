---
title: Dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a2f6381666128808ec7f655622d430e3e349c5e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101720"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: Dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do .NET Framework, usługi i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.
>
>  Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zebrać dane dotyczące wydajności usługi .NET Framework, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe. Należy ponownie uruchomić komputer, który jest hostem usługi i konfigurowanie komputera w celu profilowania. Następnie należy dołączyć profiler do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi, a następnie program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć profiler do usługi .NET Framework

1. Zainstaluj usługę.

2. Otwórz okno wiersza polecenia.

3. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** umożliwia pobieranie próbek.

   - **/samplelineoff** wyłącza przypisanie zebranych danych do określonego źródła wierszy kodu. Gdy ta opcja jest określona, dane są przypisane tylko do funkcji.

4. Uruchom ponownie komputer.

5. Otwórz okno wiersza polecenia.

6. Uruchom program profiler. Wpisz:

    **Narzędzia VSPerfCmd**[/start](../profiling/start.md) **: Przykładowe**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **/Start:sample** opcja inicjuje profiler.

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL). |

7. Jeśli to konieczne, uruchom usługę.

8. Dołącz profiler do usługi. Wpisz:

    **Narzędzia VSPerfCmd**[/ dołączanie](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Określ identyfikator procesu (`PID`) lub nazwę procesu (ProcName) usługi. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.

     Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niewstrzymanych procesora zegara cykli. Jest to około 100 próbek na sekundę w przypadku procesora 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Zdarzenie próbkowania|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:** `Interval`|Zamienia interwał próbkowania na liczbę cykli zegara niewstrzymanych określony przez `Interval`.|
   |[Timer](../profiling/pf.md)[**:**`Interval`]|Zamienia zdarzenie próbkowania na błędy stron. Jeśli `Interval` zostanie określona, ustawia liczbę błędów stron pomiędzy próbkami. Domyślna to 10.|
   |[/ sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Zamienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` zostanie określona, ustawia liczbę wywołań pomiędzy próbkami. Domyślna to 10.|
   |[/ Licznik](../profiling/counter.md) **:** `Config`|Zamienia zdarzenie próbkowania i interwał licznik wydajności procesora oraz interwał określony w `Config`.|

   - **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, można użyć *VSPerfCmd.exe* umożliwiające uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |**/ Dołączanie:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ Dołączanie** rozpoczyna się zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. Możesz odłączyć z aplikacji profilowanej przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.

 **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć program profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         —lub—

    - Typ **VSPerfCmd / Odłącz**

2. Zamknij program profilujący. Wpisz:

     **Narzędzia VSPerfCmd/shutdown**

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)