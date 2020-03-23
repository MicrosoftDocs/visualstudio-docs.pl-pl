---
title: Analizowanie zużycia energii w aplikacjach platformy uniwersalnej systemu Windows | Dokumenty firmy Microsoft
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
monikerRange: vs-2017
ms.openlocfilehash: 0fc78a84d0c2f86e8db6c4703cc7404a32508d72
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144730"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analizowanie zużycia energii w aplikacjach platformy UWP

Profiler **zużycia energii** w programie Visual Studio pomaga analizować zużycie energii i energii aplikacji platformy uniwersalnej systemu Windows na tabletach o niskim poużyciu, które działają przez cały czas lub przez część czasu na własnych bateriach. Działająca na urządzeniu zasilanym z baterii aplikacja, która zużywa zbyt dużo energii, może powodować niezadowolenia klienta, przez co klient może ją nawet odinstalować. Optymalizacja zużycia energii może zwiększyć wykorzystanie aplikacji i ich wykorzystanie przez klientów.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co to jest profiler Zużycie energii, jak działa i co mierzy

Profiler Zużycie energii przechwytuje działania wyświetlacza, procesora i połączeń sieciowych urządzenia podczas sesji profilowania. Następnie generuje szacunki zużycia mocy na potrzeby wykonania tych działań i całkowitej ilości energii dla sesji profilowania.

> [!NOTE]
> Profiler energii szacuje pobór mocy i zużycie energii, używając programowego modelu standardowego sprzętu referencyjnego, który jest reprezentatywny dla tabletów o niskim poziomie zasilania, na których może być uruchamiana dana aplikacja. Aby uzyskać najlepsze szacunki, zaleca się zbieranie danych profilu na tablecie o niskim poziomie zasilania.
>
> Chociaż model zapewnia dobre oszacowania dla różnych urządzeń o niskim poziomie zasilania, rzeczywiste wartości dotyczące profilowanego urządzenia mogą być inne. Należy użyć wartości, aby wykryć działania wyświetlacza, procesora i sieci, które są kosztowne względem innych działań wykorzystujących zasoby, i mogą nadawać się do optymalizacji.

Profiler zużycia energii wykorzystuje te definicje *energii* i *energii:*

- *Moc* mierzy szybkość, że siła jest używana do wykonywania pracy, która jest wykonywana w okresie czasu. W elektrotechnice standardową jednostką mocy jest *wat*, który jest definiowany jako szybkość, z jaką praca jest wykonywana, gdy jeden amper prądu przepływa przez różnicę potencjału elektrycznego jednego woltu. Na wykresie **Zużycie energii** jednostki są wyświetlane jako miliwaty **mW,** które są jedną tysięczną wata.

   Należy zauważyć, że moc jest stosunkiem, więc ma kierunek (praca w danym czasie może wzrosnąć lub zmaleć) i szybkość (ilość, o jaką praca rośnie lub maleje).

- *Energia* mierzy całkowitą ilość energii, albo jako pojemność lub potencjał, jak w pojemności baterii, lub jako całkowita ilość energii zużytej przez pewien okres czasu. Jednostką energii jest watogodzina, czyli moc jednego wata stosowana równomiernie przez jedną godzinę. W **podsumowaniu energetycznym**jednostki są wyświetlane jako godziny **mW-h.**

![Pojemność energetyczna, zużyta moc, całkowita zużyta energia](../profiling/media/energyprof_capcitypowerused.png)

Na przykład w pełni naładowana bateria w tablecie zawiera pewną ilość zmagazynowanej energii. Gdy energia jest zużywana na potrzeby wykonywania zadań, takich jak komunikacja przez sieć, obliczanie wartości czy wyświetlanie grafiki, moc z baterii jest zużywana z różną szybkością. Dla dowolnego okresu mierzone jest także łączne zużycie mocy.

## <a name="identify-scenarios-with-user-marks"></a>Identyfikowanie scenariuszy ze znacznikami użytkownika
 Do danych profilowania można dodać *znaczniki użytkownika,* aby ułatwić identyfikację obszarów na linijce osi czasu.

 ![Znaczniki użytkownika na osi czasu](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Znacznik jest wyświetlany na osi czasu w postaci pomarańczowego trójkąta w czasie wykonywania metody. Po umieszczeniu kursora myszy na znaczniku komunikat i czas są wyświetlane jako etykietka narzędzia. Jeśli co najmniej dwa znaczniki użytkownika znajdują się blisko siebie, są scalane, a dane etykietek narzędzia są łączone. Można powiększyć oś czasu, aby rozdzielić znaczniki.

 **Dodawanie znaczników do kodu C#, Visual Basic, C++**

 Aby dodać znacznik użytkownika do kodu C#, Visual Basic, <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> C++, należy najpierw utworzyć obiekt. Następnie wstaw <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> wywołania metod w punktach w kodzie, które chcesz oznaczyć. Użyj [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) w wywołaniach.

 Gdy jest wykonywana metoda, znacznik użytkownika jest dodawany do danych profilowania wraz z komunikatem.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType>implementuje <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> interfejs (przewidywane <xref:System.IDisposable?displayProperty=nameWithType> jak w językach C# i VB). Aby uniknąć wycieku zasobów systemu <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> operacyjnego, wywołaj (w języku C# i VB) po zakończeniu pracy z kanałem rejestrowania.
> - Każdy otwarty kanał rejestrowania musi mieć unikatową nazwę. Jeśli spróbujesz utworzyć nowy kanał rejestrowania o takiej samej nazwie jak kanał niedysponowany, zostanie zgłoszony wyjątek.

Na przykład kod można znaleźć w przykładzie Przykładowy [rejestrowanie sesji sesji sesji sesji sydaj](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)systemu Windows .

::: moniker range="vs-2017"
**Dodawanie znaczników do kodu JavaScript**

Aby dodać znaczniki użytkownika, dodaj następujący kod w punktach w kodzie, które chcesz oznaczyć:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* to ciąg zawierający komunikat wyświetlany w etykietce narzędzia znacznika użytkownika.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Konfigurowanie środowiska do profilowania
 Aby uzyskać dobre szacunki, warto profilować zużycie energii przez aplikację na urządzeniu o niskim pożyciem, które jest zasilane przez baterie. Ponieważ program Visual Studio nie działa na większości tych urządzeń, należy połączyć komputer programu Visual Studio z urządzeniem przy użyciu narzędzi zdalnych programu Visual Studio. Aby podłączyć urządzenie zdalne, należy skonfigurować zarówno projekt programu Visual Studio, jak i urządzenie zdalne. Aby uzyskać więcej informacji, zobacz Uruchamianie aplikacji platformy uniwersalnej systemu Windows na [komputerze zdalnym.](../debugger/run-windows-store-apps-on-a-remote-machine.md)

> [!TIP]
> - Nie zaleca się profilowania energii na symulatorze platformy uniwersalnej systemu Wizjudy lub na komputerze z programem Visual Studio. Profilowanie na rzeczywistym urządzeniu umożliwia uzyskanie bardziej realistycznych danych.
> - Profiluj urządzenie docelowe zasilane z baterii.
> - Zamknij inne aplikacje, które mogą używać tych samych zasobów (sieci, procesora lub wyświetlacza).

## <a name="collect-energy-profile-data-for-your-app"></a>Zbieranie danych profilu energetycznego aplikacji

1. W menu **Debugowanie** wybierz polecenie **Rozpocznij diagnostykę bez debugowania**.

     ![Wybierz zużycie energii w centrum diagnostycznym](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Wybierz pozycję **Zużycie energii,** a następnie wybierz pozycję **Start**.

    > [!NOTE]
    > Po uruchomieniu profilera **zużycia energii** może zostać wyświetlene okno Kontrola **konta użytkownika** z prośbą o pozwolenie na uruchomienie pliku *VsEtwCollector.exe*. Wybierz **pozycję Tak**.

3. Zbadaj aplikację w celu zebrania danych.

4. Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj kolekcję** na stronie Centrum diagnostyki.

     ![Zatrzymywanie zbierania danych](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Zbieranie danych profilu energetycznego zainstalowanej aplikacji
 Narzędzie Zużycie energii można uruchamiać tylko w aplikacjach platformy uniwersalnej systemu Windows, które są uruchamiane z rozwiązania programu Visual Studio lub są instalowane ze sklepu Microsoft Store. Gdy rozwiązanie jest otwarte w programie Visual Studio, domyślnym celem jest **projekt uruchamiania**. Aby określić zainstalowaną aplikację jako obiekt docelowy:

1. Wybierz **pozycję Zmień miejsce docelowe,** a następnie wybierz pozycję **Zainstalowana aplikacja**.

2. Z listy **Wybierz zainstalowany pakiet aplikacji** wybierz obiekt docelowy.

3. Wybierz **pozycję Zużycie energii** na stronie centrum diagnostyki.

4. Wybierz **pozycję Rozpocznij** profilowanie.

   Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj kolekcję** na stronie Centrum diagnostyki.

## <a name="analyze-energy-profile-data"></a>Analizowanie danych profilu energetycznego
 Dane profilu energetycznego są wyświetlane w oknie dokumentu programu Visual Studio:

 ![Strona raportu profilera energii](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Plik raportu nosi nazwę Report*YYYYMMDD-HHMM*.diagsession. Jeśli zechcesz zapisać raport, możesz zmienić jego nazwę.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Wykres **użycia energii** to wykres wieloliniowy, który wyświetla zmianę mocy wyjściowej spowodowanej zasobem urządzenia podczas sesji profilowania. Profiler Zużycie energii śledzi moc zużywaną przez procesor, działania sieciowe i wyświetlanie na ekranie.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Wykres **Zasoby (on/off)** zawiera szczegółowe informacje na temat kosztów energii sieciowej. **Pasek sieci** reprezentuje czas otwarcia połączenia sieciowego. Pasek **podrzędny transferu danych** to czas, w której aplikacja odbierała lub wysyłała dane przez sieć.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Podsumowanie zużycia energii** pokazuje proporcjonalną ilość całkowitej energii, która została użyta na wybranej osi czasu przez procesor, aktywność sieciową i ekran.|

 **Do analizy danych profilu energetycznego**

 Znajdź obszar, w którym wzrosła moc zużywana przez zasoby. Powiąż ten obszar wzrostu z działaniem aplikacji. Następnie użyj pasków sterowania na osi czasu, aby powiększyć ten obszar. Jeśli koncentrujesz się na użyciu sieci, rozwiń węzeł **sieć** na wykresie **Zasoby (On/Off),** aby porównać czas otwarcia połączenia sieciowego z czasem, w którego aplikacja odbierała lub przesyłała dane za pośrednictwem połączenia. Skrócenie czasu niepotrzebnego otwarcia połączenia sieciowego to bardzo efektywny sposób optymalizacji.

## <a name="optimize-energy-use"></a>Optymalizacja zużycia energii
 Połączenia sieciowe generują koszty energii nie tylko podczas przesyłania danych, ale także podczas inicjowania, obsługi i wyłączania połączenia. Niektóre sieci obsługują połączenie przez pewien czas po zakończeniu wysyłania lub odbierania danych, aby umożliwić transmisję większej ilości danych za pośrednictwem jednego połączenia. Za pomocą okienka **Zasoby (On/Off)** można sprawdzić, w jaki sposób aplikacja wchodzi w interakcję z połączeniem.

 ![&#40;&#41;&#47;zasoby](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Jeśli paski **transferu sieci** i **danych** pokazują, że połączenie jest otwarte przez dłuższy czas, aby sporadycznie przesyłać serię małych pakietów danych, można partią danych, aby wysłać je w jednej transmisji, skrócić czas otwarcia sieci, a tym samym zaoszczędzić koszty energii.

 ![Okienko podsumowania zużycia energii](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Koszty energii zużywanej przez wyświetlacz trudniej jest kontrolować. Większości ekranów potrzebuje więcej energii do wyświetlania jasnych kolorów niż do wyświetlania kolorów ciemniejszych, więc użycie ciemnego tła stanowi jedyny sposób zmniejszenia kosztów.

## <a name="other-resources"></a>Inne zasoby

- W sekcjach **Zarządzanie stanem połączenia i kosztami** dla [języka C#/VB/C++ i XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) opisano interfejsy API systemu Windows, które zawierają informacje o łączności sieciowej, których aplikacja może używać w celu zminimalizowania kosztów ruchu sieciowego.

   Symulator programu Visual Studio dla aplikacji platformy uniwersalnej systemu Windows umożliwia symulowanie właściwości połączenia danych interfejsów API informacji sieciowej. Zobacz [Uruchamianie aplikacji platformy uniwersalnej systemu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md)

- Narzędzia **użycia procesora CPU** mogą pomóc zmniejszyć obciążenie procesora CPU, gdy jest to spowodowane przez nieefektywne funkcje. Zobacz [Analizowanie użycia procesora .](../profiling/beginners-guide-to-performance-profiling.md)

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)