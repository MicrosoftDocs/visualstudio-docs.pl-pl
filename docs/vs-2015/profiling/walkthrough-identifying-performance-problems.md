---
title: 'Przewodnik: identyfikowanie problemów z wydajnością | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc4135b9b861a460295c67c576405edd5c63211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695013"
---
# <a name="walkthrough-identifying-performance-problems"></a>Przewodnik: identyfikowanie problemów z wydajnością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak profilować aplikację, aby identyfikować problemy z wydajnością.  
  
 W tym instruktażu opisano proces profilowania aplikacji zarządzanej oraz pobierania próbek i Instrumentacji w celu wyizolowania i zidentyfikowania problemów z wydajnością w aplikacji.  
  
 W tym instruktażu wykonasz następujące czynności:  
  
- Profilowanie aplikacji przy użyciu metody próbkowania.  
  
- Analizuj przykładowe wyniki profilowania, aby zlokalizować i rozwiązać problem z wydajnością.  
  
- Profilowanie aplikacji przy użyciu metody instrumentacji.  
  
- Analizuj instrumentację wyników profilowania, aby zlokalizować i rozwiązać problem z wydajnością.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- Pośrednia interpretacja języka C#.  
  
- Kopia [przykładu PeopleTrax —](../profiling/peopletrax-sample-profiling-tools.md).  
  
  Aby można było korzystać z informacji dostarczonych przez profilowanie, najlepszym rozwiązaniem jest udostępnienie informacji o symbolach debugowania.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania  
 Próbkowanie to metoda profilowania, za pomocą której proces jest okresowo sondowany, aby określić aktywną funkcję. Dane wynikowe zawierają informacje o tym, jak często dana funkcja znajduje się na szczycie stosu wywołań podczas próbkowania procesu.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Aby profilować aplikację przy użyciu metody próbkowania  
  
1. Otwórz [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] program z uprawnieniami administratora. Uruchomienie programu jako administrator jest wymagane do profilowania.  
  
2. Otwórz rozwiązanie PeopleTrax —.  
  
     Rozwiązanie PeopleTrax — teraz wypełnia Eksplorator rozwiązań.  
  
3. Ustaw ustawienie Konfiguracja projektu na **Zwolnij**.  
  
     Aby wykrywać problemy z wydajnością w aplikacji, należy użyć kompilacji wydania. Kompilacja wydania jest zalecana do profilowania, ponieważ Kompilacja debugowania zawiera dodatkowe informacje, które mogą mieć negatywny wpływ na wydajność i nie ilustrują dokładnie problemów z wydajnością.  
  
4. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.  
  
     Zostanie wyświetlony Kreator wydajności.  
  
5. Upewnij się, że wybrano **próbkowanie procesora (zalecane)** , a następnie kliknij przycisk **dalej**.  
  
6. W **której aplikacji chcesz kierować profilem**, wybierz pozycję PeopleTrax —, a następnie kliknij przycisk **dalej**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] kompiluje projekt i uruchamia profiluje aplikację. Zostanie wyświetlone okno aplikacji **PeopleTrax —** .  
  
7. Kliknij pozycję **Pobierz osoby**.  
  
8. Kliknij pozycję **ExportData**.  
  
     Zostanie otwarty Notatnik i zostanie wyświetlony nowy plik zawierający wyeksportowane dane z **PeopleTrax —**.  
  
9. Zamknij Notatnik, a następnie zamknij aplikację **PeopleTrax —** .  
  
     Profiler generuje plik danych profilowania ( \* . vsp), wyświetla nazwę pliku w sekcji Raporty okna Eksplorator wydajności i automatycznie ładuje widok **podsumowania** pliku danych w oknie głównym [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Aby przeanalizować przykładowe wyniki profilowania  
  
1. Widok podsumowania przedstawia oś czasu użycia procesora CPU w trakcie przebiegu profilowania, listę **ścieżek gorącą** reprezentującą gałąź drzewa wywołań aplikacji, która była najbardziej aktywna i listę **funkcji wykonujących większość poszczególnych** zadań, które pokazują funkcje, które były najbardziej silnie próbkowane podczas wykonywania kodu w ich własnej treści funkcji.  
  
     Sprawdź listę **ścieżek gorąca** i Zauważ, że metoda PeopleNS. ludzie. GetNames jest funkcją PeopleTrax — najbliżej końca listy. Jego pozycja sprawia, że jest to dobry kandydat do analizy. Kliknij nazwę funkcji, aby wyświetlić szczegóły elementu GetNames w widoku **Szczegóły funkcji** .  
  
2. Widok **Szczegóły funkcji** zawiera dwa okna. Okno Dystrybucja kosztów udostępnia widok graficzny pracy wykonanej przez funkcję, pracę wykonywaną przez wywołane funkcje oraz wkład funkcji, które wywołały funkcję, do liczby wystąpień, które były próbkowane. Można zmienić funkcję, która jest fokusem widoku, klikając nazwę funkcji. Na przykład można kliknąć pozycję PeopleNS. ludzie. getludzie, aby uniemożliwić wybranie funkcji getludzie.  
  
     W oknie **Widok kodu funkcji** jest wyświetlany kod źródłowy funkcji, jeśli jest ona dostępna i wyróżnia najbardziej kosztowne wiersze w wybranej funkcji. Po wybraniu pozycji GetNames można zobaczyć, że ta funkcja odczytuje ciąg z zasobów aplikacji, a następnie używa elementu, <xref:System.IO.StringReader> Aby dodać każdy wiersz w ciągu do obiektu <xref:System.Collections.ArrayList> . Nie istnieje oczywisty sposób na optymalizację tej funkcji.  
  
3. Ponieważ PeopleNS. ludzie. getludzie jest jedynym obiektem wywołującym GetNames, kliknij pozycję getludzie w oknie Dystrybucja kosztów, aby przeanalizować swój kod. Ta metoda zwraca <xref:System.Collections.ArrayList> PersonInformationNS. PersonInformation obiektów z nazw osób i firm utworzonych przez metodę GetNames. Jednak GetNames są wywoływane dwukrotnie za każdym razem, gdy tworzony jest obiekt PersonInformation. Można sprawdzić, czy metoda może być łatwo zoptymalizowana przez utworzenie list tylko raz na początku metody i indeksowanie na listach podczas pętli tworzenia PersonInformation.  
  
4. Alternatywna wersja elementu getludzie jest dostarczana z przykładowym kodem aplikacji i można wywołać zoptymalizowaną funkcję, dodając symbol kompilacji warunkowej do właściwości kompilacji. W oknie Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt osoby, a następnie kliknij polecenie **Właściwości**. Kliknij przycisk **Kompiluj** w menu strony właściwości, a następnie wpisz **OPTIMIZED_GETPEOPLE** w polu tekstowym symbol kompilacji warunkowej. Zoptymalizowana wersja programu getludzie zastępuje oryginalną metodę w następnej kompilacji.  
  
5. Uruchom ponownie sesję wydajności. Na pasku narzędzi Eksplorator wydajności kliknij pozycję **Uruchom z profilowania**. Kliknij pozycję **Pobierz osoby** , a następnie kliknij pozycję **Eksportuj dane**. Zamknij okno Notatnik, które zostanie wyświetlone, a następnie zamknij aplikację osoby Trax.  
  
     Zostanie wygenerowany nowy plik danych profilowania, a w oknie głównym pojawi się widok **podsumowania** dla nowych danych [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .  
  
6. Aby porównać dwa przebiegi profilowania, zaznacz dwa pliki danych w Eksplorator wydajności, kliknij plik prawym przyciskiem myszy, a następnie kliknij polecenie **PORÓWNAJ raporty wydajności**. W oknie głównym pojawi się okno Raport porównawczy [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Kolumna **Delta** pokazuje zmianę wartości wydajności funkcji z wcześniejszej wartości **bazowej** na późniejszą wartość **porównania** . Możesz wybrać wartości do porównania z listy rozwijanej **kolumny** . Wybierz pozycję **próbki włączne%**.  
  
     Zwróć uwagę, że metody getludzie i GetNames pokazują znaczny wzrost wydajności.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilowanie przy użyciu metody instrumentacji  
 Instrumentacja to metoda profilowania, w której Profiler wstawia funkcje sondowania do specjalnie utworzonych wersji plików binarnych profilowanych. Sondy zbierają informacje o chronometrażu w momencie wejścia i wyjścia z funkcji w modułach oprzyrządowanych i we wszystkich wywołaniach w tych funkcjach. Proces Instrumentacji jest przydatny do badania problemów związanych z operacjami wejścia/wyjścia, takimi jak zapisywanie na dysku i komunikowanie się przez sieć. Instrumentacja zawiera bardziej szczegółowe informacje niż próbkowanie, ale bardziej inwazyjne w wykonywaniu procesu i wiąże się z większą ilością narzutów. Instrumentacja plików binarnych jest również większa niż debugowanie lub wydanie plików binarnych i nie jest przeznaczona do wdrożenia.  
  
 W tej części przewodnika będziemy używać metody instrumentacji do odnajdywania większej ilości kodu, którą możemy zoptymalizować w aplikacji PeopleTrax —, która została wcześniej profilowana. Korzystając z filtru osi czasu widoku podsumowania, będziemy skupić się na naszej analizie scenariusza eksportu danych w profilowanej aplikacji, w której lista osób jest zapisywana w pliku Notatnika.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Aby profilować istniejącą aplikację przy użyciu metody instrumentacji  
  
1. W razie potrzeby Otwórz aplikację PeopleTrax — w programie Visual Studio.  
  
     Upewnij się, że korzystasz z programu jako administrator i że konfiguracja kompilacji dla rozwiązania jest ustawiona na wartość **Release**.  
  
2. W Eksplorator wydajności kliknij pozycję **Instrumentacja**.  
  
3. Na pasku narzędzi Eksplorator wydajności kliknij pozycję **Uruchom z profilowania**.  
  
     Profiler kompiluje projekt i zaczyna profiluje aplikację. Zostanie wyświetlone okno aplikacji PeopleTrax —.  
  
4. Kliknij pozycję **Pobierz osoby**.  
  
     Siatka danych PeopleTrax — wypełnia dane.  
  
5. Odczekaj około 10 sekund, a następnie kliknij pozycję **Eksportuj dane**.  
  
     Zostanie uruchomiony **Notatnik** i zostanie wyświetlony nowy plik zawierający listę osób z PeopleTrax —. Oczekiwanie umożliwia łatwą identyfikację procedury eksportu danych na potrzeby filtrowania.  
  
6. Zamknij **Notatnik**, a następnie zamknij aplikację **PeopleTrax —** .  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] generuje raport sesji wydajności (*. vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Aby przeanalizować wyniki profilowania Instrumentacji  
  
1. Wykres osi czasu widoku **Podsumowanie** raportu przedstawia użycie procesora przez program w czasie trwania przebiegu profilowania. Operacja eksportu danych powinna być dużym szczytem lub plateau po prawej stronie grafu. Możemy odfiltrować sesję wydajności, aby wyświetlać i analizować tylko dane, które zostały zebrane w operacji eksportowania. Kliknij z lewej strony punktu na grafie, na którym rozpoczyna się operacja eksportowania danych. Kliknij ponownie po prawej stronie operacji. Następnie kliknij przycisk **Filtruj według wyboru** na liście linków z prawej strony osi czasu.  
  
    Drzewo **ścieżki gorąca** pokazuje, że <xref:System.String.Concat%2A> Metoda wywoływana za pomocą metody PeopleTrax —. Form1. ExportData zużywa znaczną część czasu. Ponieważ **System. String. Concat** jest również w górnej części **funkcji z największą listą zadań roboczych** , skrócenie czasu poświęcanego na funkcję jest najprawdopodobniej optymalizacją.  
  
2. Kliknij dwukrotnie pozycję **System. String. Concat** w jednej z tabel podsumowujących, aby wyświetlić więcej informacji w widoku Szczegóły funkcji.  
  
3. Można zobaczyć, że PeopleTrax —. Form1. ExportData jest jedyną metodą wywołującą concat. Kliknij pozycję **PeopleTrax —. Form1. ExportData** na liście **funkcji wywołujących** , aby wybrać metodę jako element docelowy widoku szczegółów funkcji.  
  
4. Sprawdź metodę w oknie widok kodu funkcji. Zwróć uwagę, że nie ma żadnych wywołań literału do **System. String. Concat**. Zamiast tego istnieje kilka zastosowania operandu + =, który kompilator zastępuje z wywołaniami do **System. String. Concat**. Wszelkie modyfikacje ciągu w .NET Framework powodują przydzielenie nowego ciągu. .NET Framework zawiera <xref:System.Text.StringBuilder> klasę, która jest zoptymalizowana pod kątem łączenia ciągów  
  
5. Aby zamienić ten obszar problemu na zoptymalizowany kod, Dodaj OPTIMIZED_EXPORTDATA jako symbol kompilacji warunkowej do projektu PeopleTrax —.  
  
6. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt PeopleTrax —, a następnie kliknij polecenie **Właściwości**.  
  
    Zostanie wyświetlony formularz właściwości projektu PeopleTrax —.  
  
7. Kliknij kartę **kompilacja** .  
  
8. W polu tekstowym **symbole kompilacji warunkowej** wpisz **OPTIMIZED_EXPORTDATA**.  
  
9. Zamknij formularz właściwości projektu i po wyświetleniu monitu wybierz pozycję **Zapisz wszystko** .  
  
   Po ponownym uruchomieniu aplikacji zobaczysz wyróżnione ulepszenia wydajności. Zaleca się ponowne uruchomienie sesji profilowania, nawet w przypadku, gdy są widoczne ulepszenia wydajności. Przeglądanie danych po rozwiązaniu problemu jest ważne, ponieważ pierwszy problem może zasłaniać inny problem.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [/Z7,/Zi,/ZI (format informacji o debugowaniu)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)
