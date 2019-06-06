---
title: 'Instrukcje: Instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0cd767e505af7e5d503695a1e7aea65dbfe62027
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747823"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Instrukcje: Instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera

W tym artykule opisano, jak Instrumentacja usługi .NET Framework i zbieranie szczegółowych danych o chronometrażu przy użyciu narzędzia wiersza polecenia programu Visual Studio Profiling Tools.

> [!NOTE]
> Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie można uruchomić ponownie po uruchomieniu komputera, takiej usługi, który uruchamia tylko wtedy, gdy zostanie uruchomiony system operacyjny.
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.
>
> Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur za pomocą narzędzi profilowania z wiersza polecenia. Zobacz [zbierania danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Zbieranie szczegółowych danych o chronometrażu przy użyciu usługi .NET Framework przy użyciu metody instrumentacji, należy użyć [VSInstr.exe](../profiling/vsinstr.md) narzędzie, aby wygenerować instrumentowaną wersję składnika. Można następnie zastąpić nieinstrumentowaną wersję usługi z oprzyrządowaną wersją upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Możesz użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie, aby zainicjować zmienne środowiskowe globalnego profilowania, a następnie ponownie uruchom komputer-host. Następnie uruchamiasz profiler.

Gdy usługa jest uruchomiona, danych o chronometrażu są automatycznie zbierane do pliku danych. Można wstrzymywać i wznawiać zbieranie danych podczas sesji profilowania.

Aby zakończyć sesję profilowania, wyłącz usługę i następnie jawnie Zamknij profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera

1. Otwórz okno wiersza polecenia.

2. Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji pliku binarnego usługi.

3. Zastąp oryginalny plik binarny na wersję instrumentowaną. W Windows Menedżera sterowania usługami, upewnij się, że usługa typ uruchomienia ustawiono ręcznie.

4. Zainicjuj profilowanie zmiennych środowiskowych w programie .NET Framework. Wpisz:

     **VSPerfClrEnv /globaltraceon**

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom program profiler. Wpisz:

     **/ OUTPUT polecenia VSPerfCmd:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) **: śledzenia** opcja inicjuje profiler.

   - [/Output](../profiling/output.md) **:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.

     Można użyć jednego z następujących opcji z **polecenia** opcji.

     > [!NOTE]
     > **/User** i **/crosssession** opcje są zazwyczaj wymagane dla usług profilowania.

     | Opcja | Opis |
     | - | - |
     | [/ User](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows. |
     | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Sesja identyfikator jest wymieniony w **identyfikator sesji** kolumny na **procesy** kartę w Menedżerze zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
     | [/waitstart](../profiling/waitstart.md)[ **:** `Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przed zwróceniem błąd programu profiler. Jeśli `Interval` nie zostanie określony, program profiler oczekuje w nieskończoność. Domyślnie **/start** zwraca natychmiast. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z kolekcją danych jest wstrzymany, należy dodać **/globaloff** opcję **/start** wiersza polecenia. Użyj **globalon** Aby wznowić profilowanie. |
     | [/ Licznik](../profiling/counter.md) **:** `Config` | Zbiera informacje z wydajności procesora, licznik określone w konfiguracji. Informacje licznika są dodawane do danych zbieranych podczas każdego zdarzenia profilowania. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
     | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |

8. Uruchom usługę z Menedżera kontroli usług Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy usługa jest uruchomiona, można użyć *VSPerfCmd.exe* umożliwiające uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie usługi.

- Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje ( **/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia ( **/processon**) lub zatrzymuje ( **/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia ( **/threadon**) lub zatrzymuje ( **/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, Zatrzymaj usługę, w której działa składnik instrumentowany, a następnie wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania.

Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska, które mają być stosowane.

1. Zatrzymaj usługę z Menedżera kontroli usług.

2. Zamknij program profilujący. Wpisz:

     **Narzędzia VSPerfCmd/shutdown**

3. Po zakończeniu wszystkich zadań profilowania, wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Zastąp moduł instrumentowany jego oryginałem. Jeśli to konieczne, ponownie skonfiguruj typ uruchomienia usługi.

5. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także

[Profil usługi](../profiling/command-line-profiling-of-services.md)
[widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)
