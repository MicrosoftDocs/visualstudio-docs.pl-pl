---
title: Analizowanie zużycia energii w aplikacjach ze sklepu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3147a6bafc550383f96134f5a76932413eb8a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299372"
---
# <a name="analyze-energy-use-in-store-apps"></a>Analizowanie zużycia energii w aplikacjach ze Sklepu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler **zużycia energii** w programie Visual Studio pomaga analizować zużycie energii i energii przez aplikacje ze sklepu Windows na urządzeniach typu tablet z niską mocą, które są uruchamiane przez cały czas i w ich własnych bateriach. Działająca na urządzeniu zasilanym z baterii aplikacja, która zużywa zbyt dużo energii, może powodować niezadowolenia klienta, przez co klient może ją nawet odinstalować. Optymalizacja zużycia energii może zwiększyć zainteresowanie aplikacją i liczbę używających jej klientów.  
  
## <a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a>Co to jest Profiler Zużycie energii, jak działa i co mierzy  
 Profiler Zużycie energii przechwytuje działania wyświetlacza, procesora i połączeń sieciowych urządzenia podczas sesji profilowania. Następnie generuje szacunki zużycia mocy na potrzeby wykonania tych działań i całkowitej ilości energii dla sesji profilowania.  
  
> [!NOTE]
> Profiler energii szacuje pobór mocy i zużycie energii, używając programowego modelu standardowego sprzętu referencyjnego, który jest reprezentatywny dla tabletów o niskim poziomie zasilania, na których może być uruchamiana dana aplikacja. Aby uzyskać najlepsze szacunki, zaleca się zbieranie danych profilu na tablecie o niskim poziomie zasilania.  
>   
> Chociaż model zapewnia dobre oszacowania dla różnych urządzeń o niskim poziomie zasilania, rzeczywiste wartości dotyczące profilowanego urządzenia mogą być inne. Należy użyć wartości, aby wykryć działania wyświetlacza, procesora i sieci, które są kosztowne względem innych działań wykorzystujących zasoby, i mogą nadawać się do optymalizacji.  
  
 Profiler Zużycie energii używa następujących definicji *zasilania* i *energii*:  
  
- Mierzy *moc* , która jest używana do wykonywania pracy, która jest wykonywana w danym okresie czasu. W nauce elektrycznej standardową jednostką mocy jest wartość *a,* która jest definiowana jako szybkość, z jaką wykonywane jest działanie, gdy jeden Ampere prądu jest przez siłę elektryczną o wartości jeden wolt. Na wykresie **zużycie mocy** jednostki są wyświetlane jako miliwaty **MW** , które są jedną thousandthą w.  
  
   Należy zauważyć, że moc jest stosunkiem, więc ma kierunek (praca w danym czasie może wzrosnąć lub zmaleć) i szybkość (ilość, o jaką praca rośnie lub maleje).  
  
- *Energia energetyczna* mierzy całkowitą ilość mocy, jako pojemność lub potencjał, jak zużywa moc baterii lub łączną ilość mocy zużywanej w danym okresie czasu. Jednostką energii jest watogodzina, czyli moc jednego wata stosowana równomiernie przez jedną godzinę. W **podsumowaniu energii**jednostki są wyświetlane jako miliwatogodziny-hours **MW-h**.  
  
  ![Pojemność energii, użyte zużycie energii, Łączna liczba użytych energii](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Na przykład w pełni naładowana bateria w tablecie zawiera pewną ilość zmagazynowanej energii. Gdy energia jest zużywana na potrzeby wykonywania zadań, takich jak komunikacja przez sieć, obliczanie wartości czy wyświetlanie grafiki, moc z baterii jest zużywana z różną szybkością. Dla dowolnego okresu mierzone jest także łączne zużycie mocy.  
  
## <a name="BKMK_Identify_scenarios_with_user_marks"></a>Identyfikowanie scenariuszy ze znacznikami użytkownika  
 Możesz dodać *znaczniki użytkownika* do danych profilowania, aby pomóc identyfikować obszary na linijce osi czasu.  
  
 ![Znaczniki użytkownika na osi czasu](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Znacznik jest wyświetlany na osi czasu w postaci pomarańczowego trójkąta w czasie wykonywania metody. Po umieszczeniu kursora myszy na znaczniku komunikat i czas są wyświetlane jako etykietka narzędzia. Jeśli co najmniej dwa znaczniki użytkownika znajdują się blisko siebie, są scalane, a dane etykietek narzędzia są łączone. Można powiększyć oś czasu, aby rozdzielić znaczniki.  
  
 **Dodaj znaczniki do C#, Visual Basic, C++ kod**  
  
 Aby dodać znacznik użytkownika do C#, Visual Basic, C++ kod, najpierw Utwórz obiekt [Windows. Foundation. Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) . Następnie Wstaw wywołania do metody [LoggingChannel. LogMessage](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) w punktach w kodzie, które chcesz oznaczyć. Użyj [LoggingLevel. informacje](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) w wywołaniach.  
  
 Gdy jest wykonywana metoda, znacznik użytkownika jest dodawany do danych profilowania wraz z komunikatem.  
  
> [!NOTE]
> - Windows. Foundation. Diagnostics LoggingChannel implementuje interfejs [Windows. Foundation. IClosable](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) (przewidywany jako [System. IDISPOSABLE](https://msdn.microsoft.com/library/System.IDisposable.aspx) w C# i VB). Aby uniknąć przecieków zasobów systemu operacyjnego, wywołaj [LoggingChannel. Close](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx)() (Windows. Foundation. Diagnostics. LoggingChannel. Dispose () C# w i VB) po zakończeniu pracy z kanałem rejestrowania.  
>   - Każdy otwarty kanał rejestrowania musi mieć unikatową nazwę. Próba utworzenia nowego kanału rejestrowania o takiej samej nazwie, jak nazwa aktualnie otwartego kanału, powoduje wyjątek.  
  
 **Dodawanie znaczników do kodu JavaScript**  
  
 Aby dodać znaczniki użytkownika, dodaj następujący kod w punktach w kodzie, które chcesz oznaczyć:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* jest ciągiem zawierającym komunikat, który ma być wyświetlany w etykietce narzędzia znacznika użytkownika.  
  
## <a name="BKMK_Configure_your_environment_for_profiling"></a>Skonfiguruj swoje środowisko do profilowania  
 Aby uzyskać dobre szacunki, warto profilować zużycie energii przez aplikację na urządzeniu o niskim poziomie zasilania, które jest zasilane z baterii. Program Visual Studio nie działa na większości z tych urządzeń, więc należy podłączyć komputer z programem Visual Studio do urządzenia, używając narzędzi zdalnych programu Visual Studio. Aby podłączyć urządzenie zdalne, należy skonfigurować zarówno projekt programu Visual Studio, jak i urządzenie zdalne. Aby uzyskać więcej informacji [, zobacz Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md) .  
  
> [!TIP]
> - Nie zaleca się profilowania energii z użyciem symulatora Sklepu Windows ani komputera z programem Visual Studio. Profilowanie na rzeczywistym urządzeniu umożliwia uzyskanie bardziej realistycznych danych.  
>   - Profiluj urządzenie docelowe zasilane z baterii.  
>   - Zamknij inne aplikacje, które mogą używać tych samych zasobów (sieci, procesora lub wyświetlacza).  
  
## <a name="BKMK_Collect_energy_profile_data_for_your_app"></a>Zbieranie danych profilu energetycznego dla aplikacji  
  
1. W menu **debugowanie** wybierz polecenie **Uruchom diagnostykę bez debugowania**.  
  
     ![Wybieranie zużycia energii w centrum diagnostyki](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. Wybierz pozycję **zużycie energii** , a następnie wybierz polecenie **Uruchom**.  
  
    > [!NOTE]
    > Po uruchomieniu profilera **zużycia energii** może zostać wyświetlone okno **Kontrola konta użytkownika** z żądaniem uprawnienia do uruchomienia programu programu VsEtwCollector. exe. Wybierz **tak**.  
  
3. Zbadaj aplikację w celu zebrania danych.  
  
4. Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj zbieranie** na stronie centrum diagnostyki.  
  
     ![Zatrzymaj zbieranie danych](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.  
  
## <a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a>Zbieranie danych profilu energetycznego dla zainstalowanej aplikacji  
 Narzędzie Zużycie energii można uruchomić jedynie dla aplikacji do Sklepu Windows 8.1 uruchamianych z poziomu rozwiązania programu Visual Studio lub zainstalowanych ze Sklepu Windows. Gdy rozwiązanie jest otwarte w programie Visual Studio, domyślnym celem jest **projekt startowy**. Aby określić zainstalowaną aplikację jako obiekt docelowy:  
  
1. Wybierz pozycję **Zmień cel** , a następnie wybierz pozycję **zainstalowana aplikacja**.  
  
2. Z listy **Wybierz zainstalowany pakiet aplikacji** wybierz element docelowy.  
  
3. Wybierz pozycję **zużycie energii** na stronie centrum diagnostyki.  
  
4. Wybierz pozycję **Rozpocznij** , aby rozpocząć profilowanie.  
  
   Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj zbieranie** na stronie centrum diagnostyki.  
  
## <a name="BKMK_Analyze_energy_profile_data"></a>Analizowanie danych profilu energetycznego  
 Dane profilu energetycznego są wyświetlane w oknie dokumentu programu Visual Studio:  
  
 ![Strona raportu profilera energii](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Plik raportu ma nazwę Report*RRRRMMDD-hhmm*. diagsession. Jeśli zechcesz zapisać raport, możesz zmienić jego nazwę.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Wykres **zużycie mocy** jest wykresem wieloliniowym, w którym jest wyświetlana zmiana w danych wyjściowych, która jest spowodowana przez zasób urządzenia podczas sesji profilowania. Profiler Zużycie energii śledzi moc zużywaną przez procesor, działania sieciowe i wyświetlanie na ekranie.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|Wykres **zasoby (włączone/wyłączone)** zawiera szczegółowe informacje o kosztach energii sieci. Pasek **Sieć** przedstawia czas otwarcia połączenia sieciowego. **Transfer danych** pasku podrzędnym jest czas, w którym aplikacja odbierała lub wysyłała dane przez sieć.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|**Podsumowanie zużycia energii** przedstawia proporcjonalną ilość całkowitej energii, która została użyta w wybranej osi czasu przez procesor, aktywność sieci i wyświetlanie ekranu.|  
  
 **Aby przeanalizować dane profilu zasilania**  
  
 Znajdź obszar, w którym wzrosła moc zużywana przez zasoby. Powiąż ten obszar wzrostu z działaniem aplikacji. Następnie użyj pasków sterowania na osi czasu, aby powiększyć ten obszar. Jeśli planujesz użycie sieci, rozwiń węzeł **Sieć** na wykresie **zasoby (włączone/wyłączone)** , aby porównać czas otwarcia połączenia sieciowego na czas, w którym aplikacja odbierała lub przeniesie dane przez połączenie. Skrócenie czasu niepotrzebnego otwarcia połączenia sieciowego to bardzo efektywny sposób optymalizacji.  
  
## <a name="BKMK_Optimize_energy_use"></a>Optymalizacja zużycia energii  
 Połączenia sieciowe generują koszty energii nie tylko podczas przesyłania danych, ale także podczas inicjowania, obsługi i wyłączania połączenia. Niektóre sieci obsługują połączenie przez pewien czas po zakończeniu wysyłania lub odbierania danych, aby umożliwić transmisję większej ilości danych za pośrednictwem jednego połączenia. Możesz użyć okienka **zasoby (włączone/wyłączone)** , aby poznać sposób interakcji aplikacji z połączeniem.  
  
 ![Zasoby &#40;w&#47;okienku&#41; wyłączone](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Jeśli paski **sieci** i **transfer danych** pokazują, że połączenie jest otwarte przez długie okresy, aby sporadycznie przesyłać serię małych pakietów danych, można utworzyć dane wsadowe w celu wysłania ich w jednej transmisji, skrócić czas, w którym sieć jest otwarta, a tym samym zaoszczędzić koszty energii.  
  
 ![Okienko podsumowania zużycia energii](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Koszty energii zużywanej przez wyświetlacz trudniej jest kontrolować. Większości ekranów potrzebuje więcej energii do wyświetlania jasnych kolorów niż do wyświetlania kolorów ciemniejszych, więc użycie ciemnego tła stanowi jedyny sposób zmniejszenia kosztów.  
  
## <a name="BKMK_Other_resources"></a>Inne zasoby  
  
- W sekcjach **stan połączenia i zarządzanie kosztami** dla [ C#C++ /VB/i XAML](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) oraz [JavaScript i HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) w centrum deweloperów systemu Windows opisano interfejsy API systemu Windows, które zapewniają informacje o łączności sieciowej, które mogą być używane przez aplikację w celu zminimalizowania kosztu ruchu sieciowego.  
  
     Symulator aplikacji do Sklepu Windows w programie Visual Studio umożliwia symulowanie właściwości połączenia danych interfejsów API informacji sieciowych. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md)  
  
- **Chronometraż funkcji języka JavaScript** i narzędzia **użycia procesora CPU** mogą pomóc w zmniejszeniu obciążenia procesora, gdy jest ono spowodowane przez funkcje niewydajne. Zobacz [Analizowanie użycia procesora CPU](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).
