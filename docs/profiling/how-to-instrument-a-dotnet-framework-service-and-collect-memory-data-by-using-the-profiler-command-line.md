---
title: Profiler Command line-Instrumentacja .NET, pobieranie danych pamięci
description: Dowiedz się, jak za pomocą narzędzi wiersza polecenia programu Visual Studio narzędzia profilowania zbierać dane alokacji pamięci i okresu istnienia obiektów dla usługi .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 80ca26f0f68a4c717d94055d0886a8085931c900
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942675"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Instrukcje: instrumentacja usługi .NET Framework i zbieranie danych pamięci przy użyciu wiersza polecenia profilera

W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do Instrumentacji usługi .NET Framework i zbierania danych o użyciu pamięci. Można zbierać dane alokacji pamięci lub zbierać dane alokacji pamięci i okresu istnienia obiektu.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie może zostać uruchomiona ponownie po uruchomieniu komputera, taka usługa uruchamiana podczas uruchamiania systemu operacyjnego.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

## <a name="start-the-profiling-session"></a>Rozpocznij sesję profilowania
 Aby zbierać dane dotyczące wydajności z usługi .NET Framework, należy użyć narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) w celu zainicjowania odpowiednich zmiennych środowiskowych i narzędzia [VSInstr.exe](../profiling/vsinstr.md) w celu utworzenia Instrumentacji kopii pliku binarnego usługi.

 Komputer hostujący usługę musi zostać uruchomiony ponownie, aby skonfigurować profil do profilowania. Należy również ręcznie uruchomić usługę z poziomu Menedżera kontroli usług. Następnie uruchom Profiler, a następnie uruchom usługę .NET Framework.

 Po wykonaniu składnika Instrumentacji dane pamięci są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, zamknij usługę i jawnie wyłącz Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Aby rozpocząć profilowanie usługi .NET Framework

1. Otwórz okno wiersza polecenia.

2. Użyj narzędzia **VSInstr** , aby wygenerować instrumentację wersji pliku binarnego usługi.

3. Użyj menedżera kontroli usług, aby zastąpić oryginalny plik binarny wersją z instrumentacją. Upewnij się, że typ uruchamiania usługi jest ustawiony na ręczny.

4. Zainicjuj zmienne środowiskowe profilowania. Wpisz:

    **VSPerfCLREnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** i **/globaltracegclife** umożliwiają zbieranie danych alokacji pamięci i okresu istnienia obiektów.

       |Opcja|Opis|
       |------------|-----------------|
       |**/globaltracegc**|Zbiera tylko dane alokacji pamięci.|
       |**/globaltracegclife**|Zbiera dane alokacji pamięci i okresu istnienia obiektu.|

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom Profiler. Wpisz:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Opcja **/Start: contenting** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie **Identyfikator sesji** na karcie **procesy** w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ] | Określa liczbę sekund oczekiwania na zainicjowanie profilera przed zwróceniem błędu. Jeśli `Interval` nie jest określony, profiler czeka na czas nieokreślony. Domyślnie **/Start** zwraca natychmiast. |
   | [/GlobalOff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** . |
   | [/Counter](../profiling/counter.md) **:**`Config` | Zbiera informacje z licznika wydajności procesora określonego w konfiguracji. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.*ETL*). |

8. W razie potrzeby uruchom usługę.

9. Dołącz profiler do usługi. Wpisz:

     **VSPerfCmd/Attach:** `PID`&#124;`ProcessName`

    - Określ identyfikator procesu lub nazwę procesu usługi. Identyfikatory procesów i nazwy wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy usługa jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub kończy (**/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku ( `TID` ).|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, zamknij aplikację, na której działa składnik instrumentacji, a następnie uruchom opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/GlobalOff** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Zatrzymaj usługę z menedżera kontroli usług.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

3. Po ukończeniu wszystkich profilowania Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/GlobalOff**

     Zamień moduł z pakietem na oryginalny. W razie potrzeby skonfiguruj ponownie typ uruchomienia usługi.

4. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz też
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
