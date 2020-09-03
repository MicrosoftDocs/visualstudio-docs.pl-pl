---
title: 'Przewodnik: Profiler XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669524"
---
# <a name="walkthrough-xslt-profiler"></a>Przewodnik: profiler XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler XSLT tworzy szczegółowe raporty wydajności XSLT, które pomagają mierzyć, szacować i kierować problemy związane z wydajnością w kodzie XSLT. Profiler XSLT zawiera przydatne wskazówki dotyczące optymalizacji arkusza stylów XSL i XSLT. W przypadku aplikacji XSLT, które wymagają maksymalnej wydajności, to narzędzie może być niezbędne.

## <a name="prerequisites"></a>Wymagania wstępne
 Procedury opisane w poniższych instruktażu wymagają programu Visual Studio 2010 and.NET Framework w wersji 4,0. Profiler XSLT jest dostępny tylko w systemie Microsoft Visual Studio Team System z zainstalowanym narzędzia profilowania.

### <a name="create-the-performance-report"></a>Tworzenie raportu o wydajności

1. Otwórz dokument XSLT w programie Visual Studio.

2. Kliknij opcję **profil XSLT** , która jest dostępna w menu XML.

3. Podaj wejściowy dokument XML. Jeśli dokument XML nie jest jeszcze otwarty, zostanie wyświetlony monit o podanie pliku.

4. Analiza rozpocznie się, a pasek postępu wyświetla postęp w edytorze.

5. Dane wyjściowe XSLT są widoczne w okienku danych wyjściowych.

6. Po zakończeniu sesji wydajności Sprawdź raport dotyczący wydajności. Dane zapisane w raporcie wydajności umożliwiają wyświetlanie i analizowanie wydajności XSLT.

### <a name="get-all-the-available-views"></a>Pobierz wszystkie dostępne widoki

1. Kliknij listę rozwijaną **bieżący widok** , aby pobrać wszystkie dostępne widoki.

2. Wybierz opcję **Widok podsumowania** z listy rozwijanej **bieżący widok** . Raport dotyczący wydajności jest domyślnie wyświetlany w **widoku podsumowania**. Ten widok jest punktem wyjścia do określania problemów z wydajnością w dokumentach XSLT. **Widok podsumowania** zawiera następujące punkty danych:

    - Najczęściej wywoływane funkcje

    - Funkcje z największą ilością pracy

    - Wykonywanie funkcji trwa najdłuższy czas

3. Domyślnie istnieją trzy kolumny dla każdego punktu danych: nazwę funkcji, liczbę wywołań w wartości bezwzględnej i wartość procentową nazwanej funkcji do całkowitego wywołania funkcji. Z każdego punktu danych w **widoku Podsumowanie**możesz przejść do bardziej szczegółowych widoków, klikając prawym przyciskiem myszy punkty danych funkcji.

4. Wybierz opcję **Widok funkcji** z listy rozwijanej **bieżący widok** . **Widok funkcji** zawiera listę funkcji wywoływanych podczas profilowania. Dane można sortować, klikając nazwę kolumny. Domyślnie wyświetlane są następujące kolumny:

    - **Nazwa funkcji**

    - **Czas włączny, który upłynął**

    - **Czas wyłączny, który upłynął**

    - **Czas włączny aplikacji**

    - **Czas wyłączny aplikacji**

    - **Liczba połączeń**

5. Wszystkie kolumny czasu są wyświetlane zarówno jako wartości bezwzględne, jak i procentowe. **Termin ten** odnosi się do łącznego czasu, przez który funkcja wykorzystała z innych funkcji wywoływanych podczas wykonywania tej funkcji.

6. Termin " **włącznie** " dotyczy łącznego czasu wykonywania funkcji, w tym czasu wykonywania wszystkich funkcji, które wywołuje, oraz tego, czy każda z tych wywołanych funkcji nazywa się innymi funkcjami.

### <a name="select-callercallee-view"></a>Wybierz Widok wywołujący/wywoływany

1. Wybierz widok **wywołujący/wywoływany** w **bieżącym widoku** listy rozwijanej.

2. Widok **wywołujący/wywoływany** ma następujące trzy różne części:

    - **Funkcje, które wywołały**: wszystkie funkcje, które wywołały określoną funkcję, są wyświetlane w górnej części widoku.

    - **Bieżąca funkcja**: określona funkcja, która została wywołana, jest wymieniona w środkowej części widoku.

    - **Funkcje, które zostały wywołane przez** : wszystkie funkcje, które zostały wywołane przez określoną funkcję, są wyświetlane w dolnej części widoku.

3. Jeśli funkcja o nazwie `SyncToNavigator` pojawia się w środkowej części widoku, wszystkie funkcje, które wywołały `SyncToNavigator` funkcję, pojawiają się w górnej części widoku, a wszystkie funkcje, które zostały wywołane przez `SyncToNavigator` pojawiają się w dolnej części widoku.

4. Funkcję można zmienić w środkowej części widoku przez dwukrotne kliknięcie dowolnej z funkcji wymienionych w pozostałych dwóch częściach widoku. Widok zostanie następnie zaktualizowany, aby odzwierciedlić zmiany automatycznie.

5. Możesz również sortować dane, klikając pozycję nazwy kolumn.

### <a name="select-calltree-view"></a>Wybierz widok widokach drzewa wywołań

1. Wybierz pozycję **Widok drzewa wywołań** na liście rozwijanej **bieżący widok** . Ten widok jest widokiem drzewa wykonywania programu.

2. **Widok drzewa wywołań** zawiera element główny drzewa jako nazwę procesu. Funkcje są węzłami drzewa. Ten widok umożliwia przechodzenie do szczegółów określonych śladów wywołań i analizowanie, które ślady mają największy wpływ na wydajność. Widok jest podobny do **widoku stosu wywołań** dostępnego podczas debugowania. Oprócz kolumn w **widoku funkcji**, w **widoku drzewa wywołań**, istnieje dodatkowa kolumna do wyświetlania **nazwy modułu**.

3. Wybierz pozycję **znaczniki** z listy rozwijanej **bieżący widok** .

4. Za pomocą profilera SLT istnieją znaczniki, które są wyświetlane w strumieniu zbierania danych ze skojarzonym komentarzem. Znaczniki są umieszczane w kodzie, który ma liczniki. Po poinformowaniu profilera XSLT o zbieraniu liczników wydajności XSLT, liczniki są zbierane za każdym razem, gdy jeden z tych znaków zostanie wykonany. Dane są wyświetlane w tabeli zawierającej **Identyfikator znacznika**, **nazwę znacznika** (**program początkowy**, **program końcowy**) i **sygnaturę czasową**. Znaczniki nie są agregowane i wyświetlane w kolejności chronologicznej w **widoku znaczniki** raportu wydajności.

### <a name="select-modules-in-the-current-view"></a>Wybierz moduły w bieżącym widoku

1. Wybierz pozycję **moduły** z listy rozwijanej **bieżący widok** .

2. Widok modułów to płaska lista wszystkich funkcji agregowanych na poziomie modułu. Rozwiń lub Zwiń nazwę modułu, aby wyświetlić lub zamknąć widok danych wydajności modułu. Dane można sortować, klikając nazwę kolumny. Domyślnie istnieją zarówno wartości bezwzględne, jak i wartości procentowe dla **czasu**, który upłynął, **upłynął czas wyłączny** **, czas trwania aplikacji,** **wyłączny czas aplikacji**oraz **liczbę wywołań**.

3. Wybierz pozycję **proces** z listy rozwijanej **bieżący widok** .

4. Widok procesu przedstawia tabelę zawierającą **Identyfikator procesu**, **nazwę procesu**, **godzinę rozpoczęcia**i **godzinę zakończenia**. Dane można sortować, klikając pozycję nazwy kolumn.

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Korzystanie z hierarchii XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
