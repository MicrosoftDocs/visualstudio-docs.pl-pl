---
title: Analizowanie zużycia energii w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 8ecd06b2c340640db082c5d0a6bbdb6a30596748
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624415"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analizowanie zużycia energii w aplikacjach platformy uniwersalnej systemu Windows
Visual Studio **zużycie energii** profiler pomaga analizować zużycie mocy i energii w aplikacjach platformy UWP na urządzeniach tablecie o niskim poziomie zasilania, które działają ciągle lub czasu na własnych bateriach. Działająca na urządzeniu zasilanym z baterii aplikacja, która zużywa zbyt dużo energii, może powodować niezadowolenia klienta, przez co klient może ją nawet odinstalować. Optymalizacja zużycia energii może zwiększyć liczbę użytkowników w Twojej aplikacji i używany przez klientów.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co to jest profiler Zużycie energii, jak działa i co mierzy
 Profiler Zużycie energii przechwytuje działania wyświetlacza, procesora i połączeń sieciowych urządzenia podczas sesji profilowania. Następnie generuje szacunki zużycia mocy na potrzeby wykonania tych działań i całkowitej ilości energii dla sesji profilowania.

> [!NOTE]
> Profiler energii szacuje pobór mocy i zużycie energii, używając programowego modelu standardowego sprzętu referencyjnego, który jest reprezentatywny dla tabletów o niskim poziomie zasilania, na których może być uruchamiana dana aplikacja. Aby uzyskać najlepsze szacunki, zaleca się zbieranie danych profilu na tablecie o niskim poziomie zasilania.
>
> Chociaż model zapewnia dobre oszacowania dla różnych urządzeń o niskim poziomie zasilania, rzeczywiste wartości dotyczące profilowanego urządzenia mogą być inne. Należy użyć wartości, aby wykryć działania wyświetlacza, procesora i sieci, które są kosztowne względem innych działań wykorzystujących zasoby, i mogą nadawać się do optymalizacji.

 Profiler zużycie energii są używane następujące definicje *power* i *energii*:

- *Power* środki siły służy do wykonywania pracy, które odbywa się w danym okresie czasu. W naukach elektrycznych standardową jednostką mocy jest *wata*, która została zdefiniowana jako szybkość jaką praca jest wykonywana, gdy jeden ampere bieżącego przepływów za pomocą różnica potencjałów volt jeden. W **zużycia energii** wykres, jednostki są miliwaty **mW** , które są tysięczną jednego wata.

   Należy zauważyć, że moc jest stosunkiem, więc ma kierunek (praca w danym czasie może wzrosnąć lub zmaleć) i szybkość (ilość, o jaką praca rośnie lub maleje).

- *Energii* środków łączną ilość mocy, lub możliwości, tak jak pojemność mocy baterii, lub łączna wyniósł mocy pojemnościowej czasu. Jednostką energii jest watogodzina, czyli moc jednego wata stosowana równomiernie przez jedną godzinę. W **podsumowanie energii**, jednostki są wyświetlane jako miliwatogodzinach **mwh**.

  ![Pojemność energii możliwości korzystać, całkowita ilość zużytej energii](../profiling/media/energyprof_capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")

  Na przykład w pełni naładowana bateria w tablecie zawiera pewną ilość zmagazynowanej energii. Gdy energia jest zużywana na potrzeby wykonywania zadań, takich jak komunikacja przez sieć, obliczanie wartości czy wyświetlanie grafiki, moc z baterii jest zużywana z różną szybkością. Dla dowolnego okresu mierzone jest także łączne zużycie mocy.

## <a name="identify-scenarios-with-user-marks"></a>Identyfikowanie scenariuszy ze znacznikami użytkownika
 Możesz dodać *znaczniki użytkownika* do danych profilowania, aby ułatwić sobie znajdowanie obszarów na linijce osi czasu.

 ![Znaczniki użytkownika na osi czasu](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Znacznik jest wyświetlany na osi czasu w postaci pomarańczowego trójkąta w czasie wykonywania metody. Po umieszczeniu kursora myszy na znaczniku komunikat i czas są wyświetlane jako etykietka narzędzia. Jeśli co najmniej dwa znaczniki użytkownika znajdują się blisko siebie, są scalane, a dane etykietek narzędzia są łączone. Można powiększyć oś czasu, aby rozdzielić znaczniki.

 **Dodawanie znaczników do języka C#, Visual Basic kodu w języku C++**

 Aby dodać znacznik użytkownika do C#, Visual Basic, kod języka C++, należy najpierw utworzyć <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> obiektu. Następnie Wstaw wywołania <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> metod w punktach w kodzie, które chcesz oznaczyć. Użyj [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) w wywołaniach.

 Gdy jest wykonywana metoda, znacznik użytkownika jest dodawany do danych profilowania wraz z komunikatem.

> [!NOTE]
> - Loggingchannel w przestrzeni nazw Windows.Foundation.Diagnostics implementuje [Windows.Foundation.IClosable](/uwp/api/windows.foundation.iclosable) interfejsu (nazywany [System.IDisposable](/dotnet/api/system.idisposable) w języku C# i VB). Aby uniknąć przecieku zasobów systemu operacyjnego, należy wywołać [LoggingChannel.Close](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) ([Windows.Foundation.Diagnostics.LoggingChannel.Dispose](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) w języku C# i VB) po zakończeniu za pomocą funkcji rejestrowania kanał.
>  - Każdy otwarty kanał rejestrowania musi mieć unikatową nazwę. Próba utworzenia nowego kanału rejestrowania o takiej samej nazwie, jak nazwa aktualnie otwartego kanału, powoduje wyjątek.

 Zobacz przykładową zestaw SDK Windows [przykładowe LoggingSession](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) przykłady.

 **Dodawanie znaczników do kodu w języku JavaScript**

 Aby dodać znaczniki użytkownika, dodaj następujący kod w punktach w kodzie, które chcesz oznaczyć:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

 *markDescription* jest ciąg zawierający komunikat wyświetlany w etykietce narzędzia znacznika użytkownika.

## <a name="configure-your-environment-for-profiling"></a>Konfigurowanie środowiska do profilowania
 Aby uzyskać dobre szacunki, będziesz chciał profilować zużycie energii przez aplikację na niskim poziomie zasilania urządzeń, które jest zasilane z baterii. Ponieważ program Visual Studio nie działa na większości z tych urządzeń, należy podłączyć komputer Visual Studio do urządzenia przy użyciu narzędzia zdalne programu Visual Studio. Aby podłączyć urządzenie zdalne, należy skonfigurować zarówno projekt programu Visual Studio, jak i urządzenie zdalne. Zobacz [uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md) Aby uzyskać więcej informacji.

> [!TIP]
> - Nie zaleca się profilowania energii w symulatorze platformy uniwersalnej systemu Windows lub na komputerze programu Visual Studio. Profilowanie na rzeczywistym urządzeniu umożliwia uzyskanie bardziej realistycznych danych.
>   -   Profiluj urządzenie docelowe zasilane z baterii.
>   -   Zamknij inne aplikacje, które mogą używać tych samych zasobów (sieci, procesora lub wyświetlacza).

## <a name="collect-energy-profile-data-for-your-app"></a>Zbieranie danych profilu energetycznego aplikacji

1.  Na **debugowania** menu, wybierz **Rozpocznij diagnostyczne bez debugowania**.

     ![Wybierz zużycie energii w Centrum diagnostyki](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2.  Wybierz **zużycie energii** , a następnie wybierz **Start**.

    > [!NOTE]
    >  Po uruchomieniu **zużycie energii** profilera, może zostać wyświetlony **Kontrola konta użytkownika** okno z żądaniem udzielenia uprawnienia do uruchamiania *VsEtwCollector.exe*. Wybierz **tak**.

3.  Zbadaj aplikację w celu zebrania danych.

4.  Aby zatrzymać profilowanie, przełącz się do programu Visual Studio (Alt + Tab) i wybierz polecenie **Zatrzymaj Kolekcjonowanie** na stronie Centrum diagnostyki.

     ![Zatrzymaj zbieranie danych](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Zbieranie danych profilu energetycznego zainstalowanej aplikacji
 Narzędzie zużycia energii można uruchomić tylko w aplikacjach platformy uniwersalnej systemu Windows, które będą uruchamiane z poziomu rozwiązania programu Visual Studio lub zainstalowanych ze Microsoft Store. Gdy rozwiązanie jest otwarte w programie Visual Studio, domyślnym obiektem docelowym jest **projekt startowy**. Aby określić zainstalowaną aplikację jako obiekt docelowy:

1. Wybierz **Zmień cel** , a następnie wybierz **zainstalowana aplikacja**.

2. Z **Wybierz zainstalowany pakiet aplikacji** listy, wybierz obiekt docelowy.

3. Wybierz **zużycie energii** na stronie Centrum diagnostyki.

4. Wybierz **Start** aby rozpocząć profilowanie.

   Aby zatrzymać profilowanie, przełącz się do programu Visual Studio (Alt + Tab) i wybierz polecenie **Zatrzymaj Kolekcjonowanie** na stronie Centrum diagnostyki.

## <a name="analyze-energy-profile-data"></a>Analizowanie danych profilu energetycznego
 Dane profilu energetycznego są wyświetlane w oknie dokumentu programu Visual Studio:

 ![Strona raportu profiler energii](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Plik raportu ma nazwę Raport*YYYYMMDD-HHMM*.diagsession. Jeśli zechcesz zapisać raport, możesz zmienić jego nazwę.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|**Zużycia energii** wykresu jest wykres wielowierszowy, na którym są wyświetlane zmiany w mocy wyjściowej powodowane przez zasób urządzenia podczas sesji profilowania. Profiler Zużycie energii śledzi moc zużywaną przez procesor, działania sieciowe i wyświetlanie na ekranie.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|**Zasoby (włączone/wyłączone)** wykres zawiera szczegółowe informacje o sieci kosztów energii. **Sieci** pasek reprezentuje czas, który połączenie sieciowe było otwarte. **Transferu danych** pasek podrzędny jest czas, że aplikacja została odbierała lub wysyłała dane za pośrednictwem sieci.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Podsumowanie użycia energii** pokazuje proporcjonalną ilość całkowitej energii, która została użyta w wybranym czasie przez Procesor, działania sieciowe i wyświetlanie na ekranie.|

 **Aby analizować dane profilu energetycznego**

 Znajdź obszar, w którym wzrosła moc zużywana przez zasoby. Powiąż ten obszar wzrostu z działaniem aplikacji. Następnie użyj pasków sterowania na osi czasu, aby powiększyć ten obszar. Jeśli koncentrujesz się na zużyciu sieciowym, rozwiń węzeł **sieci** w węźle **zasoby (włączone/wyłączone)** wykres, aby porównać czas, który połączenie sieciowe było otwarte na czas, który aplikacja odbierała lub przesyłania dane za pośrednictwem połączenia. Skrócenie czasu niepotrzebnego otwarcia połączenia sieciowego to bardzo efektywny sposób optymalizacji.

## <a name="optimize-energy-use"></a>Optymalizacja zużycia energii
 Połączenia sieciowe generują koszty energii nie tylko podczas przesyłania danych, ale także podczas inicjowania, obsługi i wyłączania połączenia. Niektóre sieci obsługują połączenie przez pewien czas po zakończeniu wysyłania lub odbierania danych, aby umożliwić transmisję większej ilości danych za pośrednictwem jednego połączenia. Możesz użyć **zasoby (włączone/wyłączone)** okienko, aby sprawdzić, jak aplikacja korzysta z połączenia.

 ![Zasoby &#40;na&#47;poza&#41; okienko](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Jeśli **sieci** i **transferu danych** słupki pokazują, że połączenie jest otwarte przez długi czas okresowo przesyłane małe pakiety danych, wsadowego danych, aby wysłać je w jednej transmisji skrócenie czasu, który jest otwarty w sieci, a tym samym zmniejszenie kosztów energii.

 ![W okienku Podsumowanie zużycia energii](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Koszty energii zużywanej przez wyświetlacz trudniej jest kontrolować. Większości ekranów potrzebuje więcej energii do wyświetlania jasnych kolorów niż do wyświetlania kolorów ciemniejszych, więc użycie ciemnego tła stanowi jedyny sposób zmniejszenia kosztów.

## <a name="other-resources"></a>Inne zasoby

-   **Stan połączenia i zarządzanie kosztami** sekcje dla [C# / VB/C++ i XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) i [języków JavaScript i HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) w Centrum deweloperów Windows opisano interfejsy API Windows, które zapewniają informacje o łączności sieciowej, można użyć aplikacji, aby zminimalizować koszty ruchu sieciowego.

     Symulatorze programu Visual Studio dla aplikacji platformy uniwersalnej systemu Windows umożliwia symulowanie właściwości połączenia danych interfejsów API informacji sieciowych. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md)

-   **Synchronizacja funkcji JavaScript** i **użycie procesora CPU** narzędzia mogą pomóc w zmniejszeniu obciążenia Procesora, gdy jest to spowodowane przez nieefektywnie działające funkcje. Zobacz [analizowania procesora](/visualstudio/profiling/beginners-guide-to-performance-profiling).

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)