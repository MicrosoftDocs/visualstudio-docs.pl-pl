---
title: 'Wiersz polecenia profilera: Instrument .NET service, get memory data'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8697f1451e3d528ff27beb2467ff7758e04267cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775499"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Instrukcje: instrumentacja usługi .NET Framework i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzi profilowania do inrządowania usługi .NET Framework i zbierania danych użycia pamięci. Można zbierać dane alokacji pamięci lub można zbierać dane alokacji pamięci i okresu istnienia obiektu.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Nie można profilować usługi przy użyciu metody instrumentacji, jeśli nie można ponownie uruchomić usługi po uruchomieniu komputera, takiej usługi, która uruchamia się po uruchomieniu systemu operacyjnego.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

## <a name="start-the-profiling-session"></a>Rozpoczynanie sesji profilowania
 Aby zbierać dane dotyczące wydajności z usługi .NET Framework, narzędzie [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) służy do inicjowania odpowiednich zmiennych środowiskowych i narzędzia [VSInstr.exe](../profiling/vsinstr.md) w celu utworzenia instrumentalnej kopii pliku binarnego usługi.

 Komputer obsługujący usługę musi zostać ponownie uruchomiony, aby skonfigurować ją do profilowania. Należy również uruchomić usługę ręcznie z Menedżera sterowania usługami. Następnie uruchom profiler, a następnie uruchom usługę .NET Framework.

 Podczas wykonywania komponentu instrumentowanego dane pamięci są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, należy zamknąć usługę i jawnie zamknąć profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Aby rozpocząć profilowanie usługi .NET Framework

1. Otwórz okno wiersza polecenia.

2. Użyj **narzędzia VSInstr** do generowania instrumentowanych wersji usługi binarnej.

3. Użyj Menedżera sterowania usługami, aby zastąpić oryginalny plik binarny wersją instrumentamencie. Upewnij się, że typ uruchamiania usługi jest ustawiony na Ręczny.

4. Inicjowanie zmiennych środowiskowych profilowania. Wpisz:

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** i **/globaltracegclife** umożliwiają zbieranie danych alokacji pamięci i okresu istnienia obiektu.

       |Opcja|Opis|
       |------------|-----------------|
       |**/globaltracegc**|Zbiera tylko dane alokacji pamięci.|
       |**/globaltracegclife**|Zbiera alokacji pamięci i danych okresu istnienia obiektu.|

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom profiler. Wpisz:

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **rywalizacji /start:** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu ASP.NET procesu roboczego. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **Procesy** Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przez profiler, zanim zwróci błąd. Jeśli `Interval` nie zostanie określony, profiler czeka przez czas nieokreślony. Domyślnie **/start** zwraca natychmiast. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymaną kolekcją danych, dodaj opcję **/globaloff** do wiersza polecenia **/start.** Użyj **/globalon,** aby wznowić profilowanie. |
   | [/licznik](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w configu. Informacje o liczniku są dodawane do danych zebranych podczas każdego zdarzenia profilowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

8. W razie potrzeby uruchom usługę.

9. Dołącz profiler do usługi. Wpisz:

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`

    - Określ identyfikator procesu lub nazwę procesu usługi. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku za pomocą opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Rozpoczyna (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych`TID`dla wątku określonego przez identyfikator wątku ( ).|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, która jest uruchomiona składnik instrumentowany, a następnie uruchom **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. **Polecenie VSPerfClrEnv /globaloff** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zatrzymaj usługę z Menedżera sterowania usługami.

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

3. Po zakończeniu profilowania wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

     Wymień moduł oprzyrządowany na oryginalny. W razie potrzeby ponownie skonfiguruj typ uruchomienia usługi.

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
