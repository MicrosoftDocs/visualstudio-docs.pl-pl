---
title: Dołączanie profilera do aplikacji .NET w celu zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 04dcf800074476b285a07e36db5a85fa3a366585
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779132"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Jak: Dołącz profiler do aplikacji autonomicznej programu .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia

W tym artykule opisano sposób używania narzędzi wiersza polecenia Narzędzi programu Visual Studio Profiling Tools do dołączania profilera do uruchomionej autonomicznej aplikacji programu .NET Framework (klient) i zbierania danych pamięci.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

Aby dołączyć do aplikacji .NET Framework i zbierać dane pamięci, należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby zainicjować odpowiednie zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można użyć narzędzia *VSPerfCmd.exe,* aby wstrzymać i wznowić zbieranie danych.

Aby zakończyć sesję profilowania, profiler musi być odłączony od wszystkich profilowanych procesów i profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Załącz profiler

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Opcje **/samplegc** i **/samplegclife** określają, czy mają być zbierane tylko dane alokacji pamięci, czy też zbierać dane alokacji pamięci i okresu istnienia obiektu. Należy określić jedną i tylko jedną opcję.

        |Opcja|Opisy|
        |------------|------------------|
        |**/samplegc**|Zbieranie tylko danych alokacji pamięci.|
        |**/samplegclife**|Zbieranie danych alokacji pamięci i okresu istnienia obiektu.|

    - Opcja **/samplelineoff** wyłącza zbieranie danych numerów wiersza kodu źródłowego.

3. Uruchom profiler. Wpisz:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - /start [/start](../profiling/start.md)**:sample** opcja inicjuje profiler.

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

     | Opcja | Opis |
     | - | - |
     | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy w Menedżerze zadań systemu Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |

4. W razie potrzeby uruchom aplikację docelową w typowy sposób.

5. Dołącz profiler do aplikacji docelowej. Wpisz:

     **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{ `ProcName`&#124;} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

    - `PID`określa identyfikator procesu aplikacji docelowej. `ProcessName`określa nazwę procesu. Należy zauważyć, `ProcessName` że jeśli określisz i wiele procesów, które mają taką samą nazwę są uruchomione, wyniki są nieprzewidywalne. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    - **/targetclr:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie `PID`danych dla procesu określonego przez .|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który `PID` jest określony przez nazwę lub proces (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania

Aby zakończyć sesję profilowania, profiler musi być odłączony od wszystkich profilowanych procesów i profiler musi być jawnie zamknięty. Profiler można odłączyć od aplikacji, która została sprofilowana przy użyciu metody próbkowania, zamykając aplikację lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Typ **VSPerfCmd /odłączać**

         — lub —

    - Zamknij aplikację docelową.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfCmd /off**

## <a name="see-also"></a>Zobacz też

[Widoki](../profiling/command-line-profiling-of-stand-alone-applications.md)
[danych pamięci](../profiling/dotnet-memory-data-views.md) autonomicznej aplikacji profilu
