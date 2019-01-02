---
title: 'Instrukcje: Instrumentacja natywnych usług i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9a4b01cb5543da45733be05c24b8b09209107b68
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966628"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Instrukcje: Instrumentowanie usługi natywnej i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do Instrumentacji macierzystej (C/C++) usługi i zbierania szczegółowych danych o chronometrażu.  

> [!NOTE]
>  Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie można uruchomić ponownie po uruchomieniu komputera, usługa, która jest uruchamiana tylko podczas uruchamiania systemu operacyjnego.  
> 
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.
 
 Aby zebrać szczegółowe dane czasowe z macierzystej usługi używając metody instrumentacji, należy użyć [VSInstr.exe](../profiling/vsinstr.md) narzędzie, aby wygenerować instrumentowaną wersję składnika. Można następnie zastąpić nieinstrumentowaną wersję usługi z oprzyrządowaną wersją upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Następnie uruchamiasz profiler.  

 Gdy usługa jest uruchomiona, danych o chronometrażu są automatycznie zbierane do pliku danych. Można wstrzymywać i wznawiać zbieranie danych podczas sesji profilowania.  

 Aby zakończyć sesję profilowania, wyłącz usługę i następnie jawnie Zamknij profiler.  

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera  

#### <a name="to-start-profiling-a-native-service"></a>Aby rozpocząć profilowanie usługi macierzystej  

1. Otwórz okno wiersza polecenia.  

2. Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji pliku binarnego usługi.  

3. Zastąp oryginalny plik binarny na wersję instrumentowaną. W Menedżerze sterowania usługami Windows upewnij się, że usługa typ uruchomienia ustawiono ręcznie.  

4. Uruchom program profiler. Wpisz:  

    **Narzędzia VSPerfCmd** [/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

   - **Polecenia** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.  

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:**`Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przed zwróceniem błąd programu profiler. Jeśli `Interval` nie zostanie określony, program profiler oczekuje w nieskończoność. Domyślnie **/start** zwraca natychmiast. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Aby uruchomić profiler z kolekcją danych jest wstrzymany, należy dodać **/globaloff** opcję **/start** wiersza polecenia. Użyj **globalon** Aby wznowić profilowanie. |
   | [/ Licznik](../profiling/counter.md) **:** `Config` | Zbiera informacje z wydajności procesora, licznik określone w konfiguracji. Informacje licznika są dodawane do danych zbieranych podczas każdego zdarzenia profilowania. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |


5. Uruchom usługę z Menedżera kontroli usług.  

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy usługa jest uruchomiona, można użyć *VSPerfCmd.exe* umożliwiające uruchamianie i zatrzymywanie zapisywania danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie usługi.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|  

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zatrzymaj usługę, w której działa składnik instrumentowany, a następnie wywołaj **VSPerfCmd**[/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Zatrzymaj usługę z Menedżera kontroli usług.  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd/shutdown**  

3.  Zastąp moduł instrumentowany jego oryginałem. Jeśli to konieczne, ponownie skonfiguruj typ uruchomienia usługi.  

## <a name="see-also"></a>Zobacz także  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)