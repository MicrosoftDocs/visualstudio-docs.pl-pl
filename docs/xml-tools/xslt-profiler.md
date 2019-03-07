---
title: Wydajność XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ecc5482c8519ceadfe1e6d5db7880c98b3d2ceb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525482"
---
# <a name="the-xslt-profiler"></a>The XSLT Profiler

Profiler XSLT tworzy szczegółowe raporty wydajności XSLT, które ułatwiają pomiar i docelowe problemy związane z wydajnością w kodzie XSLT i oceny. Profiler XSLT obejmuje, przydatne wskazówki dotyczące optymalizacji o arkusza stylów XSL i XSLT. Dla aplikacji XSLT tego żądanie uzyskania maksymalnej wydajności to narzędzie może być istotne.

Profiler XSLT jest częścią programu Visual Studio i jest dostępny na **XML** menu.

![Profiler XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Profiler XSLT jest dostępna tylko w wersji Enterprise programu Visual Studio.

## <a name="create-a-performance-report"></a>Tworzenie raportu wydajności

1. Otwórz dokument XSLT, ale w programie Visual Studio.

2. Na pasku menu wybierz **XML** > **XSLT profilu**.

3. Podaj wprowadź dokument XML. Jeśli dokument XML nie jest jeszcze otwarty, użytkownik jest monitowany dla pliku.

   Analiza zostanie uruchomiony, pasek postępu wyświetlany postęp w edytorze. Dane wyjściowe XSLT jest także widoczny.

4. Sprawdź raport wydajności do analizowania wydajności XSLT, po zakończeniu sesji wydajności.

## <a name="get-all-available-views"></a>Pobierz wszystkie dostępne widoki

1. Kliknij pozycję **bieżący widok** listy rozwijanej, aby uzyskać wszystkie dostępne widoki.

2. Wybierz **Widok Podsumowanie** opcji **bieżący widok** listy rozwijanej. Domyślnie raport wydajności jest wyświetlana w **Widok Podsumowanie**. Ten widok jest punktem wyjścia do określenia problemów z wydajnością za pomocą dokumentów XSLT. **Widok Podsumowanie** Wyświetla następujących punktów danych:

   - Funkcje wywoływane najczęściej

   - Funkcje z największą ilością indywidualnej pracy

   - Funkcje zajmujące najwięcej czasu do wykonania

   Domyślnie, istnieją trzy kolumny dla każdego punktu danych: Nazwa funkcji, liczba wywołań w wartościach bezwzględnych i wartość procentową o nazwie funkcji do wywołania całej funkcji. Z każdym danych do punktu w **Widok Podsumowanie**, możesz przejść do bardziej szczegółowych widoków przez kliknięcie prawym przyciskiem myszy punkty danych funkcji.

3. Wybierz **widoku funkcji** opcji **bieżący widok** listy rozwijanej. **Widoku funkcji** Wyświetla listę funkcji, wywoływany podczas profilowania. Dane można sortować, klikając nazwę kolumny. Kolumny domyślnie wyświetlane są:

    - **Nazwa funkcji**

    - **Całkowity czas, który upłynął**

    - **Czas wyłączny, który upłynął**

    - **Całkowity czas aplikacji**

    - **Własny czas aplikacji**

    - **Liczba wywołań**

   Wszystkie kolumny godziny są wyświetlane zarówno w przypadku wartości bezwzględne, jak i wartości procentowe. Termin **wyłączne** odwołuje się do całkowitego czasu funkcji wykonywania zużyte, z wyłączeniem czasu poświęconego przez inne funkcje wywoływane podczas wykonywania tej funkcji.

   Termin **włącznie** odwołuje się do całkowity czas funkcję wykonywania, w tym czas wykonywania wszystkich funkcji, o nazwie oraz tego, czy którakolwiek z tych nazywane funkcjami o nazwie innych funkcji.

## <a name="select-callercallee-view"></a>Wybierz widok wywołujący/wywoływany

Wybierz **wywołujący/wywoływany** wyświetlać w **bieżący widok** listy rozwijanej. **Wywołujący/wywoływany** widok ma trzy oddzielne części:

- **Funkcje, które wywołały**: Wszystkie funkcje, które wywołuje określoną funkcję znajduje się w górnej części widoku.

- **Bieżąca funkcja**: Konkretną funkcję, która została wywołana znajduje się w środkowej części widoku.

- **Funkcje, które zostały wywołane przez**: Wszystkie funkcje, które zostały wywołane przez konkretną funkcję znajduje się w dolnej części widoku.

Jeśli funkcja o nazwie `SyncToNavigator` pojawia się w środkowej części widoku, funkcje, które wywoływały `SyncToNavigator` funkcji są wyświetlane w górnej części widoku, a wszystkie funkcje, które zostały wywołane przez `SyncToNavigator` są wyświetlane w dolnej części widoku.

- Funkcja w środkowej części widoku można zmienić, klikając dwukrotnie dowolny z wymienionych w dwóch częściach widoku funkcji. Widok jest następnie aktualizowany automatycznie zgodnie ze zmianami.

- Można również sortować dane, klikając nazw kolumn.

## <a name="select-call-tree-view"></a>Wybierz widok drzewa wywołań

- Wybierz **widok drzewa wywołań** w **bieżący widok** listy rozwijanej. Ten widok jest widok drzewa wykonywania programu.

   **Widok drzewa wywołań** pokazuje drzewa jako nazwę procesu. Funkcje są węzły drzewa. Ten widok umożliwia przejście do śledzenia wywołań i analizować śledzenia, które mają największy wpływ na wydajność. Widok przypomina **widoku stosu wywołań** dostępne podczas debugowania. Oprócz kolumn w **widoku funkcji**w **widok drzewa wywołań**, ma dodatkową kolumnę do wyświetlenia **Nazwa modułu**.

- Wybierz **znaczniki** w **bieżący widok** listy rozwijanej.

   Profiler XSLT istnieją znaczniki, które pojawiają się w strumieniu zbierania danych z komentarzem skojarzone. Znaczniki są miejsca w kodzie, które mają liczników. W przypadku Poinformuj Profiler XSLT można zebrać liczników wydajności XSLT liczniki Pobierz zbierane za każdym razem, gdy jeden z tych znaków pobiera wykonywane. Dane są wyświetlane w tabeli zawierające **Identyfikator znacznika**, **Nazwa znacznika** (**Uruchom Program**, **Program zakończenia**), a  **Sygnatury czasu**. Znaki nie są agregowane i wyświetlane w kolejności chronologicznej w **widoku znaczniki** raportu wydajności.

## <a name="select-modules-in-the-current-view"></a>Wybierz moduł w bieżącym widoku

- Wybierz **modułów** w **bieżący widok** listy rozwijanej.

   Widok modułów jest płaską listę wszystkich funkcji agregowane na poziomie modułu. Rozwiń lub Zwiń Nazwa modułu do wyświetlania lub zamknąć widok danych dotyczących wydajności modułu. Dane można sortować, klikając nazwę kolumny. Domyślnie istnieją zarówno wartości bezwzględne, jak i numery procent **upłynęło całkowity czas**, **, który upłynął czas wyłączny**, **całkowity czas aplikacji**, **Własny czas aplikacji**, i **liczbę wywołań**.

- Wybierz **procesu** w **bieżący widok** listy rozwijanej.

   Widok procesu przedstawia tabelę, która zawiera **identyfikator procesu**, **nazwy procesu**, **czas rozpoczęcia**i **czas zakończenia**. Dane można sortować, klikając nazw kolumn.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Korzystanie z hierarchii XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)