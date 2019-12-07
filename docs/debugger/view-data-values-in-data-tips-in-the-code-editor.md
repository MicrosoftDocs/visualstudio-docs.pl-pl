---
title: Wyświetlanie wartości zmiennych w DataTips | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f121c7aadb605e6eb87089556ddaf1b1f4999dbb
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903890"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Podgląd wartości danych w DataTips w edytorze kodu

DataTips zapewniają wygodny sposób wyświetlania informacji na temat zmiennych w programie podczas debugowania. DataTips działa tylko w trybie przerwania i tylko w przypadku zmiennych, które znajdują się w bieżącym zakresie wykonywania. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="work-with-datatips"></a>Praca z DataTips

Etykietki danych są wyświetlane tylko w trybie przerwania, a tylko w zmiennych, które znajdują się w bieżącym zakresie wykonywania.

### <a name="display-a-datatip"></a>Wyświetl etykietki danych

1. Ustaw punkt przerwania w kodzie, a następnie rozpocząć debugowanie, naciskając klawisz **F5** lub wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Po wstrzymaniu w punkcie przerwania, umieść kursor nad dowolnej zmiennej w bieżącym zakresie. Pojawi się DataTip przedstawiający nazwę i bieżącą wartość zmiennej.

### <a name="make-a-datatip-transparent"></a>Przezroczyste etykietki danych

Aby DataTip przezroczyste, aby wyświetlić kod, który znajduje się poniżej znajduje się w DataTip, naciśnij klawisz **Ctrl**. DataTip pozostaje przezroczysty, tak długo, jak przytrzymaniu wciśniętego **Ctrl** klucza. To nie działa dla etykietki danych przypięte lub zmiennoprzecinkową.
### <a name="pin-a-datatip"></a>Numer PIN etykietki danych

Aby przypiąć etykietki danych pozostaje otwarty, wybierz pinezkę **Przypnij do źródła** ikony.

![Przypinanie elementu etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "Numer PIN etykietki danych")

Możesz przenieść etykietki danych przypięte przez przeciągnięcie go w całym okna kodu. Ikona pinezki pojawia się na marginesie obok wiersza, który DataTip jest przypięta do.

>[!NOTE]
>Etykietki danych są zawsze obliczane w kontekście, w którym wykonanie programu jest zawieszone, nie bieżący kursor lub lokalizacji DataTip. Po umieszczeniu wskaźnika myszy nad zmienną w innej funkcji, która ma taką samą nazwę jak zmienna w bieżącym kontekście, jest wyświetlana wartość zmiennej w bieżącym kontekście.

### <a name="unpin-a-datatip-from-source"></a>Odepnij etykietki danych ze źródła

Aby przestawić etykietki danych przypięte, umieść kursor nad DataTip, a następnie wybierz ikonę pinezki z menu kontekstowego.

Ikona pinezki zmienia się na pozycji odpięte i DataTip teraz liczby zmiennoprzecinkowe lub mogą być przeciągnięte przede wszystkim otwarte okna. DataTips zmiennoprzecinkową zamknięte po zakończeniu sesji debugowania.

### <a name="repin-a-datatip"></a>Repin etykietki danych

Aby repin zmiennoprzecinkowy etykietki danych do źródła, kursor w edytorze kodu i wybierz ikonę pinezki. Ikona pinezki zmienia się na pozycji przypięty i DataTip jest ponownie przypięte tylko do okna kodu.

Jeśli DataTip jest liczb zmiennoprzecinkowych za pośrednictwem oknie kodu-source, Ikona Pinezka jest niedostępna i nie może być repinned DataTip. Dostępu ikonę pinezki, zwróć DataTip oknem edytora kodu, przez przeciągnięcie go lub zapewniając fokusu okna kodu.

### <a name="close-a-datatip"></a>Zamknij etykietki danych

Aby zamknąć DataTip, umieść kursor nad DataTip, a następnie wybierz pozycję zamknięcia (**x**) ikonę z menu kontekstowego.

### <a name="close-all-datatips"></a>Zamknij wszystkie etykietki danych

Aby zamknąć wszystkie etykietki danych, na **debugowania** menu, wybierz opcję **wyczyść wszystkie etykietki danych**.

### <a name="close-all-datatips-for-a-specific-file"></a>Zamknij wszystkie etykietki danych dla określonego pliku

Aby zamknąć wszystkie etykietki danych dla określonego pliku na **debugowania** menu, wybierz opcję **wyczyść wszystkie etykietki danych przypięte do \<nazwa pliku >** .

## <a name="expand-and-edit-information"></a>Rozwiń węzeł i edytować informacje o
Korzystanie z DataTips, aby rozwinąć tablica, struktury lub obiekt, aby wyświetlić jego składowe. Można również edytować wartość zmiennej w poradzie dotyczącej danych.

### <a name="expand-a-variable"></a>Rozwiń zmienną

Aby rozwinąć obiektu w poradzie dotyczącej danych, aby wyświetlić jego elementy, umieść kursor nad strzałki rozwiń przed nazwami elementów, aby wyświetlić elementy w formie drzewa. Etykietki danych przypięte, można wybrać **+** przed zmienna nazwy, a następnie rozwiń węzeł drzewa.

![Rozwiń element etykietki danych](../debugger/media/dbg-tour-data-tips.png "Rozwiń element etykietki danych")

Można przenieść w górę i w dół w widoku rozszerzonym, można użyć myszy lub klawiszy strzałek na klawiaturze.

Możesz również przypiąć rozwiniętych elementów do przypiętych etykietka danych, przenosząc kursor myszy nad nimi i wybierając ich ikony pinezki. Elementy są wyświetlane w DataTip przypiętych następnie, po drzewie jest zwinięta.

### <a name="edit-the-value-of-a-variable"></a>Przejdź do edycji wartości zmiennej

Aby edytować wartość zmiennej lub elementu w poradzie dotyczącej danych, wybierz wartość, wpisz nową wartość i naciśnij klawisz **Enter**. Wybieranie jest wyłączone dla wartości tylko do odczytu.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips-supported-in-visual-studio-2019-version-164-preview-3-or-higher"></a>Przypnij właściwości w etykietkach danych (obsługiwane w programie Visual Studio 2019 w wersji 16,4 Preview 3 lub nowszej)

> [!NOTE]
> Ta funkcja jest obsługiwana w przypadku platformy .NET Core 3,0 lub nowszej.

Możesz szybko sprawdzić obiekty według ich właściwości w etykietkach danych za pomocą narzędzia **Pinnable Properties** .  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz ikonę pinezki, która jest wyświetlana, lub kliknij prawym przyciskiem myszy i wybierz opcję **Przypnij element członkowski jako ulubiony** w menu kontekstowym.  Powoduje to odfiltrowanie tej właściwości do górnej części listy właściwości obiektu, a nazwa właściwości i wartość są wyświetlane w prawej kolumnie etykietki danych.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję **Odepnij członka jako ulubioną** w menu kontekstowym.

![Przypinanie właściwości w etykietki danych](../debugger/media/basic-pin-datatip.gif "Przypinanie właściwości w etykietki danych")

Można również przełączać nazwy właściwości i odfiltrować przypięte właściwości podczas wyświetlania listy właściwości obiektu w etykietki danych.  Możesz uzyskać dostęp do dowolnej opcji, klikając prawym przyciskiem myszy wiersz zawierający właściwość i wybierając pozycję **Pokaż tylko przypiętych członków** lub **Ukryj nazwy przypiętych elementów członkowskich w** opcjach wartości w menu kontekstowym.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Wizualizuj złożone typy danych

Ikonę szkła powiększającego obok zmienna lub element DataTip oznacza, że jeden lub więcej [wizualizatorów](../debugger/create-custom-visualizers-of-data.md), takich jak [Wizualizator tekstu](../debugger/string-visualizer-dialog-box.md), są dostępne dla zmiennej. Wizualizatory wyświetlić informacje w sposób bardziej zrozumiały, czasami graficznego.

Aby wyświetlić element przy użyciu domyślnego wizualizatora dla typu danych, wybierz ikonę lupy ikona ![wizualizatora](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora"). Wybierz strzałkę obok ikony lupy dokonania wyboru z listy wizualizatorów typu danych.

## <a name="add-a-variable-to-a-watch-window"></a>Dodaj zmienną w oknie czujki

Jeśli chcesz obejrzeć zmiennej w dalszym ciągu możesz dodać go do **Obejrzyj** poradzie dotyczącej danych w oknie Pomoc. Kliknij prawym przyciskiem myszy na zmiennej w DataTip, a następnie wybierz pozycję **Dodaj czujkę**.

Zmienna jest wyświetlana w **Obejrzyj** okna. Jeśli Twoja wersja programu Visual Studio obsługuje więcej niż jedną **Obejrzyj** , zmienna zostanie wyświetlone w **Czujka 1**.

## <a name="import-and-export-datatips"></a>Importowanie i eksportowanie etykietki danych

Możesz wyeksportować etykietek danych do pliku XML, który można udostępniać lub edytować za pomocą edytora tekstów. Można również zaimportować plik XML etykietki danych zostały odebrane lub edytować.

**Aby wyeksportować etykietek danych:**

1. Wybierz **debugowania** > **Eksportuj etykietki danych**.

1. W **Eksportuj etykietki danych** okno dialogowe, przejdź do lokalizacji, aby zapisać plik XML, wpisz nazwę pliku, a następnie wybierz pozycję **Zapisz**.

**Aby zaimportować etykietek danych:**

1. Wybierz **debugowania** > **Importuj etykietki danych**.

1. W **Importuj etykietki danych** oknie dialogowym Wybierz plik etykietki danych XML, który chcesz otworzyć, a następnie wybierz **Otwórz**.

## <a name="see-also"></a>Zobacz także
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Techniki i narzędzia debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
