---
title: Dołącz profiler do aplikacji platformy .NET w celu zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e9aa6bcc89f0a9fb39d2a871119a0906b4243d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637948"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: Dołączanie profilera do aplikacji autonomicznej .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia

W tym artykule opisano, jak używać narzędzi wiersza polecenia programu Visual Studio Profiling Tools do dołączenia programu profilującego do uruchomionej aplikacji autonomicznej (klienta) .NET Framework i zbieranie danych pamięci.

> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

Aby dołączyć do aplikacji .NET Framework i pamięci zbierania danych, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, możesz użyć *VSPerfCmd.exe* narzędzie, aby wstrzymywać i wznawiać zbieranie danych.

Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do działającej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - **/Samplegc** i **/samplegclife** opcji można określić, czy do zbierania tylko dane alokacji pamięci lub zbierać zarówno alokacji pamięci, jak i danych o okresie istnienia obiektu. Należy określić jeden i tylko jedna opcja.

        |Opcja|Opisy|
        |------------|------------------|
        |**/samplegc**|Zbieraj tylko dane alokacji pamięci.|
        |**/samplegclife**|Zbieranie alokacji pamięci oraz danych o okresie istnienia obiektu.|

    - **/Samplelineoff** opcja wyłącza kolekcję danych numeru wiersza kodu źródłowego.

3. Uruchom program profiler. Wpisz:

     **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: Przykładowe** opcja inicjuje profiler.

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.


     | Opcja | Opis |
     | - | - |
     | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows. |
     | [/ crosssession &#124; skróconej/CS](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |


4. Jeśli to konieczne, uruchom aplikację docelową w typowy sposób.

5. Dołącz profiler do aplikacji docelowej. Wpisz:

     **Narzędzia VSPerfCmd**[/ dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i działa wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.

    - **/ targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez `PID`.|
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. Możesz odłączyć profiler od aplikacji, która była profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub przez wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.

### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Typ **VSPerfCmd / Odłącz**

         —lub—

    - Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **Narzędzia VSPerfCmd / off**

## <a name="see-also"></a>Zobacz także

[Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
[widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)