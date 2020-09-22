---
title: Dołącz profiler do platformy .NET w celu zbierania danych pamięci
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 88b3eedf8989b4c7421ecb7504b18997058a0204
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811113"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji autonomicznej .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia

W tym artykule opisano sposób używania narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania do dołączania profilera do uruchomionej .NET Framework aplikacji autonomicznej (klient) i zbierania danych pamięci.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

Aby dołączyć do aplikacji .NET Framework i zebrać dane pamięci, należy użyć narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować odpowiednie zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można użyć narzędzia *VSPerfCmd.exe* , aby wstrzymywać i wznawiać zbieranie danych.

Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCLREnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Opcje **/samplegc** i **/samplegclife** określają, czy mają być zbierane tylko dane alokacji pamięci, czy mają być zbierane dane alokacji pamięci i okresu istnienia obiektu. Należy określić jedną i tylko jedną opcję.

        |Opcja|Znajduje|
        |------------|------------------|
        |**/samplegc**|Zbiera tylko dane alokacji pamięci.|
        |**/samplegclife**|Zbieraj dane alokacji pamięci i okresu istnienia obiektu.|

    - Opcja **/samplelineoff** wyłącza zbieranie danych numeru wiersza kodu źródłowego.

3. Uruchom Profiler. Wpisz:

     **VSPerfCmd/Start: przykład/Output:** `OutputFile` [`Options`]

   - Polecenie [/Start](../profiling/start.md)**: Sample** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

     | Opcja | Opis |
     | - | - |
     | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
     | [/CrossSession &#124;/CS](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
     | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
     | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |

4. W razie potrzeby Uruchom aplikację docelową w typowy sposób.

5. Dołącz profiler do aplikacji docelowej. Wpisz:

     **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

    - `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    - **/targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określony przez `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania

Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. Można odłączyć Profiler od aplikacji, która została profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Wpisz **VSPerfCmd/detach**

         -lub-

    - Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd/off**

## <a name="see-also"></a>Zobacz też

[Profile aplikacji](../profiling/command-line-profiling-of-stand-alone-applications.md) 
 autonomicznych [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
