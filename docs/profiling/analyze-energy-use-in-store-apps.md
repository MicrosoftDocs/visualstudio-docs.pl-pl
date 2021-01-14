---
title: Analizowanie zużycia energii w aplikacjach platformy UWP | Microsoft Docs
description: Użyj profilera zużycia energii w programie Visual Studio, aby analizować zapotrzebowanie na energię i moc aplikacji platformy UWP działających na urządzeniach zasilanych z baterii.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cf55035ba5a05917334b2192067a3273f4930775
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205791"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analizowanie zużycia energii w aplikacjach platformy UWP

Profiler **zużycia energii** w programie Visual Studio pomaga analizować zużycie energii i energii przez aplikacje platformy UWP na urządzeniach typu tablet z niską mocą, które są uruchamiane przez cały czas i w ich własnych bateriach. Działająca na urządzeniu zasilanym z baterii aplikacja, która zużywa zbyt dużo energii, może powodować niezadowolenia klienta, przez co klient może ją nawet odinstalować. Optymalizacja zużycia energii może zwiększyć jego wdrożenie i użycie przez klientów.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co to jest profiler Zużycie energii, jak działa i co mierzy

Profiler Zużycie energii przechwytuje działania wyświetlacza, procesora i połączeń sieciowych urządzenia podczas sesji profilowania. Następnie generuje szacunki zużycia mocy na potrzeby wykonania tych działań i całkowitej ilości energii dla sesji profilowania.

> [!NOTE]
> Profiler energii szacuje pobór mocy i zużycie energii, używając programowego modelu standardowego sprzętu referencyjnego, który jest reprezentatywny dla tabletów o niskim poziomie zasilania, na których może być uruchamiana dana aplikacja. Aby uzyskać najlepsze szacunki, zaleca się zbieranie danych profilu na tablecie o niskim poziomie zasilania.
>
> Chociaż model zapewnia dobre oszacowania dla różnych urządzeń o niskim poziomie zasilania, rzeczywiste wartości dotyczące profilowanego urządzenia mogą być inne. Należy użyć wartości, aby wykryć działania wyświetlacza, procesora i sieci, które są kosztowne względem innych działań wykorzystujących zasoby, i mogą nadawać się do optymalizacji.

Profiler Zużycie energii używa następujących definicji *zasilania* i *energii*:

- Mierzy *moc* , która jest używana do wykonywania pracy, która jest wykonywana w danym okresie czasu. W nauce elektrycznej standardową jednostką mocy jest wartość *a,* która jest definiowana jako szybkość, z jaką wykonywane jest działanie, gdy jeden Ampere prądu jest przez siłę elektryczną o wartości jeden wolt. Na wykresie **zużycie mocy** jednostki są wyświetlane jako miliwaty **MW** , które są jedną thousandthą w.

   Należy zauważyć, że moc jest stosunkiem, więc ma kierunek (praca w danym czasie może wzrosnąć lub zmaleć) i szybkość (ilość, o jaką praca rośnie lub maleje).

- *Energia energetyczna* mierzy całkowitą ilość mocy, jako pojemność lub potencjał, jak zużywa moc baterii lub łączną ilość mocy zużywanej w danym okresie czasu. Jednostką energii jest watogodzina, czyli moc jednego wata stosowana równomiernie przez jedną godzinę. W **podsumowaniu energii** jednostki są wyświetlane jako miliwatogodziny-hours **MW-h**.

![Pojemność energii, użyte zużycie energii, Łączna liczba użytych energii](../profiling/media/energyprof_capcitypowerused.png)

Na przykład w pełni naładowana bateria w tablecie zawiera pewną ilość zmagazynowanej energii. Gdy energia jest zużywana na potrzeby wykonywania zadań, takich jak komunikacja przez sieć, obliczanie wartości czy wyświetlanie grafiki, moc z baterii jest zużywana z różną szybkością. Dla dowolnego okresu mierzone jest także łączne zużycie mocy.

## <a name="identify-scenarios-with-user-marks"></a>Identyfikowanie scenariuszy ze znacznikami użytkownika
 Możesz dodać *znaczniki użytkownika* do danych profilowania, aby pomóc identyfikować obszary na linijce osi czasu.

 ![Znaczniki użytkownika na osi czasu](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 Znacznik jest wyświetlany na osi czasu w postaci pomarańczowego trójkąta w czasie wykonywania metody. Po umieszczeniu kursora myszy na znaczniku komunikat i czas są wyświetlane jako etykietka narzędzia. Jeśli co najmniej dwa znaczniki użytkownika znajdują się blisko siebie, są scalane, a dane etykietek narzędzia są łączone. Można powiększyć oś czasu, aby rozdzielić znaczniki.

 **Dodawanie znaczników do języka C#, Visual Basic, kodu C++**

 Aby dodać znacznik użytkownika do języka C#, Visual Basic, kod C++, najpierw Utwórz <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> obiekt. Następnie Wstaw wywołania do <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> metod w punktach w kodzie, które chcesz oznaczyć. Użyj [LoggingLevel. informacje](xref:Windows.Foundation.Diagnostics.LoggingLevel) w wywołaniach.

 Gdy jest wykonywana metoda, znacznik użytkownika jest dodawany do danych profilowania wraz z komunikatem.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> implementuje <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> interfejs (przewidywany <xref:System.IDisposable?displayProperty=nameWithType> w języku C# i VB). Aby uniknąć przecieków zasobów systemu operacyjnego, <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> należy wywołać ( <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> w języku C# i VB) po zakończeniu pracy z kanałem rejestrowania.
> - Każdy otwarty kanał rejestrowania musi mieć unikatową nazwę. Jeśli podjęto próbę utworzenia nowego kanału rejestrowania o tej samej nazwie co niedysponowany kanał, zostanie zgłoszony wyjątek.

Przykładowy kod można znaleźć w Windows SDK przykład [LoggingSession](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)Sample.

::: moniker range="vs-2017"
**Dodawanie znaczników do kodu JavaScript**

Aby dodać znaczniki użytkownika, dodaj następujący kod w punktach w kodzie, które chcesz oznaczyć:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* jest ciągiem zawierającym komunikat, który ma być wyświetlany w etykietce narzędzia znacznika użytkownika.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Konfigurowanie środowiska do profilowania
 Aby uzyskać dobre oszacowania, należy profilować zużycie energii przez aplikację na urządzeniu z niską ilością zasilania, które jest zasilane z baterii. Ponieważ program Visual Studio nie działa na większości tych urządzeń, należy podłączyć komputer z programem Visual Studio do urządzenia przy użyciu narzędzi zdalnych programu Visual Studio. Aby podłączyć urządzenie zdalne, należy skonfigurować zarówno projekt programu Visual Studio, jak i urządzenie zdalne. Aby uzyskać więcej informacji [, zobacz Uruchamianie aplikacji platformy UWP na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md) .

> [!TIP]
> - Nie zalecamy profilowania energii w symulatorze platformy UWP ani na komputerze z Visual Studio. Profilowanie na rzeczywistym urządzeniu umożliwia uzyskanie bardziej realistycznych danych.
> - Profiluj urządzenie docelowe zasilane z baterii.
> - Zamknij inne aplikacje, które mogą używać tych samych zasobów (sieci, procesora lub wyświetlacza).

## <a name="collect-energy-profile-data-for-your-app"></a>Zbieranie danych profilu energetycznego aplikacji

1. W menu **debugowanie** wybierz polecenie **Uruchom diagnostykę bez debugowania**.

     ![Wybieranie zużycia energii w profilerze wydajności](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Wybierz pozycję **zużycie energii** , a następnie wybierz polecenie **Uruchom**.

    > [!NOTE]
    > Po uruchomieniu profilera **zużycia energii** może zostać wyświetlone okno **Kontrola konta użytkownika** z prośbą o zgodę na uruchomienie *VsEtwCollector.exe*. Wybierz opcję **tak**.

3. Zbadaj aplikację w celu zebrania danych.

4. Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj zbieranie** na stronie centrum diagnostyki.

     ![Zatrzymaj zbieranie danych](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Zbieranie danych profilu energetycznego zainstalowanej aplikacji
 Narzędzie zużycie energii można uruchomić tylko w przypadku aplikacji platformy UWP uruchamianych z rozwiązania programu Visual Studio lub instalowanych z Microsoft Store. Gdy rozwiązanie jest otwarte w programie Visual Studio, domyślnym celem jest **projekt startowy**. Aby określić zainstalowaną aplikację jako obiekt docelowy:

1. Wybierz pozycję **Zmień cel** , a następnie wybierz pozycję **zainstalowana aplikacja**.

2. Z listy **Wybierz zainstalowany pakiet aplikacji** wybierz element docelowy.

3. Wybierz pozycję **zużycie energii** na stronie profilera wydajności.

4. Wybierz pozycję **Rozpocznij** , aby rozpocząć profilowanie.

   Aby zatrzymać profilowanie, przełącz się z powrotem do programu Visual Studio (Alt + Tab) i wybierz pozycję **Zatrzymaj zbieranie** na stronie centrum diagnostyki.

## <a name="analyze-energy-profile-data"></a>Analizowanie danych profilu energetycznego
 Dane profilu energetycznego są wyświetlane w oknie dokumentu programu Visual Studio:

 ![Strona raportu profilera energii](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|Image (Obraz)|Opis|
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Plik raportu ma nazwę Report *RRRRMMDD-hhmm*. diagsession. Jeśli zechcesz zapisać raport, możesz zmienić jego nazwę.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Wykres **zużycie mocy** jest wykresem wieloliniowym, w którym jest wyświetlana zmiana w danych wyjściowych, która jest spowodowana przez zasób urządzenia podczas sesji profilowania. Profiler Zużycie energii śledzi moc zużywaną przez procesor, działania sieciowe i wyświetlanie na ekranie.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Wykres **zasoby (włączone/wyłączone)**  zawiera szczegółowe informacje o kosztach energii sieci. Pasek **Sieć** przedstawia czas otwarcia połączenia sieciowego. **Transfer danych** pasku podrzędnym jest czas, w którym aplikacja odbierała lub wysyłała dane przez sieć.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Podsumowanie zużycia energii** przedstawia proporcjonalną ilość całkowitej energii, która została użyta w wybranej osi czasu przez procesor, aktywność sieci i wyświetlanie ekranu.|

 **Aby przeanalizować dane profilu zasilania**

 Znajdź obszar, w którym wzrosła moc zużywana przez zasoby. Powiąż ten obszar wzrostu z działaniem aplikacji. Następnie użyj pasków sterowania na osi czasu, aby powiększyć ten obszar. Jeśli planujesz użycie sieci, rozwiń węzeł **Sieć** na wykresie **zasoby (włączone/wyłączone)**  , aby porównać czas otwarcia połączenia sieciowego na czas, w którym aplikacja odbierała lub przeniesie dane przez połączenie. Skrócenie czasu niepotrzebnego otwarcia połączenia sieciowego to bardzo efektywny sposób optymalizacji.

## <a name="optimize-energy-use"></a>Optymalizacja zużycia energii
 Połączenia sieciowe generują koszty energii nie tylko podczas przesyłania danych, ale także podczas inicjowania, obsługi i wyłączania połączenia. Niektóre sieci obsługują połączenie przez pewien czas po zakończeniu wysyłania lub odbierania danych, aby umożliwić transmisję większej ilości danych za pośrednictwem jednego połączenia. Możesz użyć okienka **zasoby (włączone/wyłączone)** , aby poznać sposób interakcji aplikacji z połączeniem.

 ![&#40;&#47;&#41; zasobów](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Jeśli paski **sieci** i **transfer danych** pokazują, że połączenie jest otwarte przez długie okresy, aby sporadycznie przesyłać serię małych pakietów danych, można utworzyć dane wsadowe w celu wysłania ich w jednej transmisji, skrócić czas, w którym sieć jest otwarta, a tym samym zaoszczędzić koszty energii.

 ![Okienko podsumowania zużycia energii](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Koszty energii zużywanej przez wyświetlacz trudniej jest kontrolować. Większości ekranów potrzebuje więcej energii do wyświetlania jasnych kolorów niż do wyświetlania kolorów ciemniejszych, więc użycie ciemnego tła stanowi jedyny sposób zmniejszenia kosztów.

## <a name="other-resources"></a>Inne zasoby

- W sekcjach **stan połączenia i zarządzanie kosztami** dla [języka C#/VB/C + + i XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) opisano interfejsy API systemu Windows, które zapewniają informacje o łączności sieciowej, które mogą być używane przez aplikację w celu zminimalizowania kosztu ruchu sieciowego.

   Program Visual Studio symulator for platformy UWP Apps umożliwia symulowanie właściwości połączenia danych interfejsów API informacji o sieci. Zobacz [Uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md)

- Narzędzia **użycia procesora CPU** mogą pomóc w zmniejszeniu obciążenia procesora, gdy jest ono spowodowane przez funkcje niewydajne. Zobacz [Analizowanie użycia procesora CPU](../profiling/beginners-guide-to-performance-profiling.md).

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)