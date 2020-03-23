---
title: Dołączanie profilera do usługi .NET w celu zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 94ea4f38ccebc1015419e2254b06033fa17a09a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777021"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi .NET w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzi profilowania do dołączania profilera do usługi .NET Framework i zbierania danych pamięci. Można zbierać dane dotyczące liczby i rozmiaru alokacji pamięci, a także zbierać dane dotyczące okresu istnienia obiektów pamięci.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Aby zbierać dane pamięci z usługi .NET Framework, należy użyć narzędzia [VSPerfCLREnv.cmd,](../profiling/vsperfclrenv.md) aby zainicjować odpowiednie zmienne środowiskowe na komputerze obsługującym usługę. Aby skonfigurować go do profilowania, należy ponownie uruchomić komputer.

 Następnie użyj [narzędzia VSPerfCmd,](../profiling/vsperfcmd.md) aby dołączyć profiler do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi być odłączony od usługi i profiler musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Załącz profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć profiler do usługi .NET Framework

1. W razie potrzeby zainstaluj usługę.

2. Otwórz okno wiersza polecenia.

3. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - Opcje **/globalsamplegclife** i **/globalsamplegclife** określają typ danych pamięci do zbierania. Określ jedną i tylko jedną z następujących opcji.

     **/globalsamplegc** Umożliwia zbieranie danych alokacji pamięci.

     **/globalsamplegclife** Umożliwia zbieranie danych alokacji pamięci i danych okresu istnienia obiektu.

   - Opcja **/samplelineoff** wyłącza zbieranie danych numerów wiersza kodu źródłowego.

4. Uruchom ponownie komputer, aby ustawić nową konfigurację środowiska.

5. W razie potrzeby uruchom usługę.

6. Otwórz okno wiersza polecenia. W razie potrzeby dodaj ścieżkę profilera do zmiennej środowiskowej PATH.

7. Uruchom profiler. Wpisz:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/start:sample** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć jednej lub więcej z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa opcjonalną domenę i nazwę użytkownika konta logowania, na którym działa usługa. Konto logowania jest wyświetlane w kolumnie Logowanie jako usługi w Menedżerze sterowania usługami systemu Windows. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |

8. Dołącz profiler do usługi. Wpisz:

    **VSPerfCmd**[/attach](../profiling/attach.md) `PID` **:**{ `ProcName`&#124;} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   - Określ identyfikator procesu lub nazwę procesu usługi. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - **targetclr:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, można użyć opcji *PROGRAMU VSPerfCmd.exe,* aby zatrzymać i rozpocząć zapisywanie danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |**/attach:**`PID` {&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** rozpoczyna zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z aplikacji profilowane za pomocą metody próbkowania, zatrzymując usługę lub wywołując **VSPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana, dopóki komputer nie zostanie ponownie uruchomiony.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         — lub —

    - Typ **VSPerfCmd /odłączać**

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
