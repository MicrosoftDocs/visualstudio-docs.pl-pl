---
title: Dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji
description: Użyj Visual Studio narzędzia profilowania wiersza polecenia, aby dołączyć profiler do usługi .NET Framework i uzyskać statystyki wydajności przy użyciu metody próbkowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 92b5e24100e43a6a03352c49111226298160521b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385477"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano sposób narzędzia profilowania wiersza polecenia w celu dołączenia profilera do usługi .NET Framework i zbierania statystyk wydajności przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian sposobu zbierania danych na tych platformach przez Visual Studio profilera zabezpieczeń. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz Performance Tools on Windows 8 and Windows Server 2012 applications (Narzędzia do Windows 8 [i aplikacji systemu Windows Server 2012).](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz Temat Określanie ścieżki [do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać ją do samego polecenia.
>
> Dodawanie danych interakcji między warstwami do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi profilowania wiersza polecenia. Zobacz [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Aby zbierać dane wydajności z .NET Framework, należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby zainicjować odpowiednie zmienne środowiskowe. Następnie należy ponownie uruchomić komputer, który hostuje usługę, i skonfigurować ten komputer do profilowania. Następnie dołącz profilera do procesu usługi. Po dołączeniu profilera do usługi można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi, a profiler musi zostać jawnie zamknięty. W większości przypadków zalecamy wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołączanie profilera

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć profiler do .NET Framework usługi

1. Zainstaluj usługę.

2. Otwórz okno wiersza polecenia.

3. Zaimicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon umożliwia** próbkowanie.

   - **/samplelineoff** wyłącza przypisanie zebranych danych do określonych wierszy kodu źródłowego. Jeśli ta opcja jest określona, dane są przypisywane tylko do funkcji.

4. Uruchom ponownie komputer.

5. Otwórz okno wiersza polecenia.

6. Uruchom profilera. Wpisz:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:sample** opcja inicjuje profilera.

   - **/Output: opcja jest** `OutputFile` wymagana z **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (vsp).

     Z opcją **/start:sample** można użyć dowolnej z następujących opcji.

   > [!NOTE]
   > **Opcje /user** **i /crosssession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem profilowany proces. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy systemu Windows Menedżer zadań. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie Procesy systemu Windows Menedżer zadań. **/CS** można określić jako skrót **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Należy używać tylko **z /wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie Śledzenie zdarzeń systemu Windows (ETW) ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (etl). |

7. W razie potrzeby uruchom usługę.

8. Dołącz profilera do usługi. Wpisz:

    **VSPerfCmd**[/attach:](../profiling/attach.md)  {&#124;} [ ] `PID` [ `ProcName` `Sample Event` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Określ identyfikator procesu `PID` () lub nazwę procesu (ProcName) usługi. Można wyświetlić identyfikatory procesów i nazwy wszystkich uruchomionych procesów w systemie Windows Menedżer zadań.

     Domyślnie dane wydajności są próbkowane co 10 000 000 niestrzymanych cykli zegara procesora. Jest to około 100 próbek na sekundę na procesorze 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niestrzymanych cykli zegara określony przez `Interval` .|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy stron. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Zmienia zdarzenie próbkowania do wywołań systemowych z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` określono wartość , określa liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenia i interwał próbkowania licznika wydajności procesora i interwał określony w `Config` .|

   - **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy w aplikacji jest ładowana więcej niż jedna wersja środowiska uruchomieniowego. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, możesz użyć *VSPerfCmd.exe,* aby rozpocząć i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wielokrotnie.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia **(/globalon**) lub zatrzymuje **(/globaloff)** zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna **(/processon**) lub zatrzymuje **(/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach** zaczyna zbierać dane dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie zostanie określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi zostać jawnie zamknięty. Możesz odłączyć element od aplikacji profilowane przy użyciu metody próbkowania, zamykając aplikację lub wywołując **opcję /detach vsPerfCmd.** Następnie wywołaj opcję **VSPerfCmd /shutdown,** aby wyłączyć profiler i zamknąć plik danych profilowania.

 Polecenie **VSPerfClrEnv /globaloff** powoduje wyczyszczenie zmiennych środowiskowych profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         -lub-

    - Typ **VSPerfCmd /detach**

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilów](../profiling/command-line-profiling-of-services.md)
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
