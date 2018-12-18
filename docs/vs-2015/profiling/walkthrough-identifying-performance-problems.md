---
title: 'Przewodnik: Identyfikowanie problemów z wydajnością | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d26e6ccabcdff12b8f4d9839888e17dc1ab3ce4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745369"
---
# <a name="walkthrough-identifying-performance-problems"></a>Przewodnik: Identyfikowanie problemów z wydajnością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób profilu aplikacji można zidentyfikować problemy z wydajnością.  
  
 W tym instruktażu będą kroków procesu profilowanie aplikacji zarządzanych i za pomocą próbkowania i instrumentacji, aby izolować i zidentyfikować problemy z wydajnością w aplikacji.  
  
 W tym instruktażu będą wykonaj następujące kroki:  
  
-   Profil aplikacji przy użyciu metody próbkowania.  
  
-   Analizuj próbkowanych wyniki profilowania, aby zlokalizować i rozwiązać problem z wydajnością.  
  
-   Profil aplikacji przy użyciu metody instrumentacji.  
  
-   Analizuj instrumentowanych wyniki profilowania, aby zlokalizować i rozwiązać problem z wydajnością.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- Pośredni znajomości języka C#.  
  
- Kopię [peopletrax — przykład](../profiling/peopletrax-sample-profiling-tools.md).  
  
  Aby pracować z danymi dostarczonych przez profilowanie, najlepiej jest mieć debugowania dostępnych informacji o symbolach.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania  
 Próbkowanie jest metodą profilowania za pomocą którego w danym procesie okresowo wysyłane do określenia funkcji active. Dane wynikowe zapewnia liczenie częstotliwość funkcja danego znajdowała się na szczycie stosu wywołań proces był wtedy próbkowany.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Aby profilować aplikację przy użyciu metody próbkowania  
  
1.  Otwórz [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] z uprawnieniami administratora. Uruchomione z uprawnieniami administratora jest wymagana dla profilowania.  
  
2.  Otwórz rozwiązanie peopletrax —.  
  
     Rozwiązanie peopletrax — teraz wypełnia Eksploratora rozwiązań.  
  
3.  Ustawienia projektu konfiguracji **wersji**.  
  
     Należy użyć kompilację wydania do wykrywania problemów z wydajnością w aplikacji. Kompilację wydania jest zalecane w przypadku profilowania, ponieważ Kompilacja debugowania ma dodatkowe skompilowane do niego informacje, które może niekorzystnie wpłynąć na wydajność i nie pokazują problemy z wydajnością, dokładnie.  
  
4.  Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.  
  
     Zostanie wyświetlony Kreator wydajności.  
  
5.  Upewnij się, że **próbkowania Procesora (zalecane)** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
6.  W **aplikacji, które chcesz docelowe dla profilowania**peopletrax — wybierz, a następnie kliknij przycisk **dalej**.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] tworzy projekt i uruchamia profilowanie aplikacji. **Peopletrax —** pojawi się okno aplikacji.  
  
7.  Kliknij przycisk **Pobierz osoby**.  
  
8.  Kliknij przycisk **ExportData**.  
  
     Notatnik otwiera i wyświetla nowy plik, który zawiera wyeksportowane dane z **peopletrax —**.  
  
9. Zamknij Notatnik, a następnie Zamknij **peopletrax —** aplikacji.  
  
     Program profilujący generuje danych profilowania (\*.vsp) plik, wyświetla nazwę pliku, w sekcji raporty w oknie Eksploratora wydajności i automatycznie ładuje **Podsumowanie** widok pliku danych w głównym oknie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Aby analizować próbkowane wyniki profilowania  
  
1.  Widok podsumowania przedstawia oś czasu użycia procesora CPU w trakcie profilowania, **ścieżka aktywna** listy, który reprezentuje gałęzi drzewa wywołań aplikacji, która był najbardziej aktywna i listę  **Działa w sposób najbardziej samodzielnej pracy** pokazujący funkcje, które zostały poddane próbkowaniu największe obciążenie podczas wykonywania kodu w treści funkcji.  
  
     Sprawdź **ścieżka aktywna** listy i Zauważ, że metoda PeopleNS.People.GetNames funkcja peopletrax — najbliższe końca listy. Jego pozycja sprawia, że dobrym kandydatem do analizy. Kliknij nazwę funkcji, aby wyświetlić szczegóły GetNames w **Szczegóły funkcji** widoku.  
  
2.  **Szczegóły funkcji** widok zawiera dwa okna. Okno podziału kosztów zawiera graficzne przedstawienie pracy wykonanej przez funkcję, pracy wykonanej przez funkcje, które go wywołały i wkład funkcje, które wywołały funkcję, aby liczba wystąpień, które zostały poddane próbkowaniu. Możesz zmienić funkcję, która jest celem widoku, klikając nazwę funkcji. Na przykład możesz kliknąć PeopleNS.People.GetPeople się GetPeople wybranej funkcji.  
  
     **Widok kodu funkcji** okno zawiera kod źródłowy funkcji, jeśli jest dostępny i wyróżnia najbardziej kosztowne wiersze w wybranej funkcji. Po wybraniu GetNames widać, ta funkcja odczytuje ciąg z zasobów aplikacji, a następnie używa <xref:System.IO.StringReader> można dodać każdy wiersz w ciągu, aby <xref:System.Collections.ArrayList>. Brak można w sposób jednoznaczny zoptymalizować tę funkcję.  
  
3.  Ponieważ PeopleNS.People.GetPeople jest tylko obiekt wywołujący GetNames, kliknij przycisk GetPeople w okno podziału kosztów, aby zbadać jego kod. Ta metoda zwraca <xref:System.Collections.ArrayList> PersonInformationNS.PersonInformation obiektów z nazwy osób i firm produkowane przez GetNames. Jednak GetNames jest wywoływana dwa razy każdym razem, który jest tworzony obiekt PersonInformation. Aby zobaczyć, metoda może zostać łatwo zoptymalizowany przez utworzenie listy tylko raz na początku metody i indeksowania w tych list, podczas tworzenia pętli PersonInformation.  
  
4.  Alternatywnej wersji cyklu GetPeople znajduje się z przykładowym kodem aplikacji i dodając symbol kompilacji warunkowej do właściwości kompilacji może być wywołanie funkcji zoptymalizowane. W oknie Eksploratora rozwiązań kliknij prawym przyciskiem myszy projekt osób, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **kompilacji** na menu strony właściwości, a następnie wpisz **OPTIMIZED_GETPEOPLE** w polu tekstowym symbol kompilacji warunkowej. Zoptymalizowana wersja GetPeople zastępuje oryginalną metodę w następnej kompilacji.  
  
5.  Należy ponownie uruchomić sesję wydajności. Kliknij na pasku narzędzi Eksploratora wydajności **uruchamianie z profilowaniem**. Kliknij przycisk **uzyskać osób** a następnie kliknij przycisk **Eksport danych**. Zamknij okno programu Notatnik, które zostanie wyświetlone, a następnie zamknij aplikację Trax osób.  
  
     Jest generowany nowy plik danych profilowania, a **Podsumowanie** nowe dane są wyświetlane w widoku [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] głównego okna.  
  
6.  Aby porównać dwa uruchomienia profilowania, wybierz pliki dwóch danych w Eksploratorze wydajności, kliknij prawym przyciskiem myszy pliki, a następnie kliknij **Porównaj wydajność raportów**. Zostanie wyświetlone okno Raport porównawczy w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] głównego okna. **Delta** zmiany w kolumnie jest wyświetlana w wartości wydajności funkcji z wcześniej **linii bazowej** wartość do późniejszej **porównania** wartość. Można wybrać wartości do porównania z **kolumny** listy rozwijanej. Wybierz **% Włącznych próbek**.  
  
     Należy zauważyć, że metody GetPeople i GetNames Pokaż wzrost wydajności znaczące.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilowanie za pomocą metody Instrumentacji  
 Instrumentacja jest metody profilowania, w którym program profilujący wstawia sondy funkcje do specjalnie utworzone wersje profilowanych danych binarnych. Sondy zbierać informacje o czasie wejścia i wyjścia funkcje w modułach instrumentowane i wszystkie witryny wywołania tych funkcji. Proces Instrumentacji jest przydatne w przypadku badania problemów związanych z operacji wejścia/wyjścia, takich jak zapisywania na dysku i komunikacji za pośrednictwem sieci. Instrumentacja zawiera więcej szczegółowych informacji niż próbkowanie, ale jest bardziej natrętnych proces wykonywania i ponosi większej ilości obciążenia. Instrumentowane pliki binarne są również większych niż Debuguj lub zwolnij pliki binarne i nie są przeznaczone do wdrożenia.  
  
 W tej części instruktażu użyjemy metody Instrumentacji Aby odnaleźć więcej kodu, które firma Microsoft można zoptymalizować w aplikacji peopletrax —, którą firma Microsoft profilowane wcześniej. Za pomocą filtru w widoku podsumowania osi czasu, skupimy się naszej analizy od scenariusza danych eksportu w nasze profilowanej aplikacji, w którym listy osób, są zapisywane do pliku Notatnika.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Aby przeprowadzić profilowanie istniejącej aplikacji przy użyciu metody Instrumentacji  
  
1.  Jeśli to konieczne, należy otworzyć aplikację peopletrax — w programie Visual Studio.  
  
     Upewnij się, że działasz jako Administrator oraz że konfiguracja kompilacji dla rozwiązania jest ustawiona na **wersji**.  
  
2.  W Eksploratorze wydajności kliknij **Instrumentacji**.  
  
3.  Kliknij na pasku narzędzi Eksploratora wydajności **uruchamianie z profilowaniem**.  
  
     Program profilujący tworzy projekt i uruchamia profilowanie aplikacji. Zostanie wyświetlone okno aplikacja peopletrax —.  
  
4.  Kliknij przycisk **Pobierz osoby**.  
  
     Peopletrax — Siatka danych zostaną wyświetlone wszystkie dane.  
  
5.  Poczekaj około 10 sekund, a następnie kliknij przycisk **Eksport danych**.  
  
     **Notatnik** rozpoczyna się i wyświetla nowy plik, który zawiera listę użytkowników z peopletrax —. Oczekiwanie umożliwia aby łatwiej zidentyfikować dane są eksportowane procedury w celu filtrowania.  
  
6.  Zamknij **Notatnik**, a następnie Zamknij **peopletrax —** aplikacji.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] generuje raport sesji wydajności (*.vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Aby analizować Instrumentacji wyniki profilowania  
  
1. Wykres osi czasu **Podsumowanie** widok raportu przedstawia wykorzystanie procesora CPU programu na czas trwania profilowania wykonywania. Operacji eksportowania danych powinien być duże szczytowe lub że po prawej stronie wykresu. Możemy filtrować sesji wydajności, aby wyświetlać i analizować dane, które zostały zebrane w ramach operacji eksportowania. Kliknij, aby po lewej stronie punktu na wykresie, gdzie rozpoczyna się operacji eksportowania danych. Kliknij ponownie, aby wykonać operację po prawej stronie. Następnie kliknij przycisk **filtru według zaznaczenia** na liście łącza z prawej strony na osi czasu.  
  
    **Ścieżka aktywna** drzewa pokazują, że <xref:System.String.Concat%2A> metodę, która jest wywoływana przez metodę PeopleTrax.Form1.ExportData zużywa duże wartości procentowej czasu. Ponieważ **System.String.Concat** jest również, w górnej części **funkcje za pomocą najbardziej samodzielnej pracy** listy, skracając czas spędzony w funkcji jest prawdopodobnie punktem optymalizacji.  
  
2. Kliknij dwukrotnie **System.String.Concat** w podsumowania tabel, aby uzyskać więcej informacji, w widoku szczegółów funkcji.  
  
3. Aby zobaczyć, że PeopleTrax.Form1.ExportData jest jedyną metodą, która wywołuje Concat. Kliknij przycisk **PeopleTrax.Form1.ExportData** w **podczas wywoływania funkcji** listę, aby wybrać metodę jest jako obiektu docelowego widoku szczegółów funkcji.  
  
4. Sprawdź metodę w oknie Widok kodu funkcji. Należy zauważyć, że nie istnieją żadne literału wywołania **System.String.Concat**. Zamiast tego ma kilka zastosowań += argument operacji, które kompilator zamienia na wywołania **System.String.Concat**. Wszelkie zmiany w ciągu w .NET Framework spowodować, że nowy ciąg do przydzielenia. Program .NET Framework zawiera <xref:System.Text.StringBuilder> klasę, która jest zoptymalizowana pod kątem ciągów  
  
5. Aby zastąpić ten obszar problemu zoptymalizowany kod, należy dodać OPTIMIZED_EXPORTDATA jako symbole kompilacji warunkowej do projektu peopletrax —.  
  
6. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt peopletrax — a następnie kliknij przycisk **właściwości**.  
  
    Zostanie wyświetlony formularz peopletrax — właściwości projektu.  
  
7. Kliknij przycisk **kompilacji** kartę.  
  
8. W **symbole kompilacji warunkowej** polu tekstowym **OPTIMIZED_EXPORTDATA**.  
  
9. Zamknij formularz Właściwości projektu i wybierz polecenie **Zapisz wszystko** po wyświetleniu monitu.  
  
   Należy ponownie uruchomić aplikację, zobaczysz oznaczone poprawę wydajności. Zaleca się uruchomienie sesji profilowania, nawet jeśli występują użytkownika widoczne poprawę wydajności. Ważne jest przeglądania danych po rozwiązaniu problemu, ponieważ pierwszy problem może zasłaniać jakiś inny problem.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Format informacji o debugowaniu)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)



