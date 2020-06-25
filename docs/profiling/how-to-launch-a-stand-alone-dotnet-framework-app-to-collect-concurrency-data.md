---
title: Wiersz polecenia profilera — Otwieranie aplikacji klienckiej platformy .NET, pobieranie danych współbieżności
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: e2c1b0a52429e74ad35cf0cad3acc44d064c9672
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327900"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: uruchamianie autonomicznej aplikacji .NET Framework z profilerem w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do uruchamiania .NET Framework autonomicznej aplikacji (klienta) i zbierania danych współbieżności procesu i wątku

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby uruchomić aplikację docelową .NET Framework przy użyciu profilera, należy użyć *VSPerfClrEnv.exe* , aby ustawić .NET Framework zmienne profilowania. Następnie należy użyć opcji VSPerfCmd **/Start** i **przełącznik/Launch** w celu zainicjowania profilera i uruchomienia aplikacji. W pojedynczym wierszu polecenia można określić wartości **/Start** i **przełącznik/Launch** oraz ich odpowiednie opcje. Możesz również dodać opcję **/GlobalOff** do wiersza polecenia, aby wstrzymać zbieranie danych podczas uruchamiania aplikacji docelowej. Następnie należy użyć **/GlobalOn** w osobnym wierszu polecenia, aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom Profiler. Wpisz:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/Output:** `OutputFile` [ `Options` ]

   - Opcja [/Start](../profiling/start.md) inicjuje profiler.

     | | |
     |-------------------------------------| - |
     | **/Start: współbieżność** | Umożliwia zbieranie danych rywalizacji o zasoby i wykonywanie wątków. |
     | **/Start: współbieżność, resourceonly** | Włącza zbieranie tylko danych rywalizacji o zasoby. |
     | **/Start: współbieżność, threadonly** | Włącza zbieranie tylko danych wykonawczych wątku. |

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile`Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Za pomocą opcji **/Start: współbieżność** można użyć dowolnej z następujących opcji.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `domain\` ]`username` | Określa opcjonalną nazwę domeny i użytkownika konta, z którym ma zostać udzielony dostęp do profilera. |
   | [/CrossSession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |

3. Uruchom aplikację docelową. Wpisz:

    **VSPerfCmd**  [przełącznik/Launch](../profiling/launch.md) **:** `AppName` [ `Options` ] [ `Sample Event` ]

    W przypadku opcji **przełącznik/Launch** można użyć dowolnej z następujących opcji.

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
   |[/Console](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

1. Poniższe pary opcji *VSPerfCmd.exe* uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ) lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych współbieżności, zamykając profilowaną aplikację lub wywołując opcję **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej.

    - Zamknij aplikację docelową.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamykanie profilera

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz też
- [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
