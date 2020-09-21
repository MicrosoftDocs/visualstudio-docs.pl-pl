---
title: Dołączanie profilera do usługi .NET w celu zbierania danych pamięci
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 50a77d3cc8d2bb3df73542b273ec3697e0a9ccd9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811074"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-service-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do usługi .NET Framework i zbierania danych pamięci. Można zbierać dane o liczbie i rozmiarze alokacji pamięci. można również zbierać dane dotyczące okresu istnienia obiektów pamięci.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Aby zbierać dane pamięci z usługi .NET Framework, należy użyć narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) w celu zainicjowania odpowiednich zmiennych środowiskowych na komputerze, który hostuje usługę. Aby skonfigurować profil do profilowania, należy ponownie uruchomić komputer.

 Następnie użyj narzędzia [VSPerfCmd](../profiling/vsperfcmd.md) , aby dołączyć Profiler do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi i musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączyć Profiler do usługi .NET Framework

1. W razie potrzeby zainstaluj usługę.

2. Otwórz okno wiersza polecenia.

3. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv** {**/globalsamplegc/globalsamplegclife**} [**/samplelineoff**]

   - Opcje **/globalsamplegclife** i **/globalsamplegclife** określają typ danych pamięci do zebrania. Określ jedną i tylko jedną z następujących opcji.

     **/globalsamplegc** Włącza zbieranie danych alokacji pamięci.

     **/globalsamplegclife** Umożliwia zbieranie danych dotyczących danych alokacji pamięci i okresu istnienia obiektu.

   - Opcja **/samplelineoff** wyłącza zbieranie danych numeru wiersza kodu źródłowego.

4. Uruchom ponownie komputer, aby ustawić nową konfigurację środowiska.

5. W razie potrzeby uruchom usługę.

6. Otwórz okno wiersza polecenia. W razie potrzeby dodaj ścieżkę profilera do zmiennej środowiskowej PATH.

7. Uruchom Profiler. Wpisz:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: przykład**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Polecenie **/Start: Sample** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć co najmniej jednej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa opcjonalną nazwę domeny i użytkownika konta logowania, w ramach którego jest uruchomiona usługa. Konto logowania jest wymienione w kolumnie Logowanie jako usługi w Menedżerze sterowania usługami systemu Windows. |
   | [/CrossSession&#124;CS](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl). |

8. Dołącz profiler do usługi. Wpisz:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Określ identyfikator procesu lub nazwę procesu usługi. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

   - **targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, możesz użyć opcji *VSPerfCmd.exe* , aby zatrzymać i uruchomić zapisywanie danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych z aplikacji profilowanej przy użyciu metody próbkowania przez zatrzymanie usługi lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfCLREnv/GlobalOff** polecenie czyści zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do momentu ponownego uruchomienia komputera.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/GlobalOff**

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
