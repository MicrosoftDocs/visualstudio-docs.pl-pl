---
title: Wyświetlanie wartości zmiennych w etykietkach danych | Microsoft Docs
description: Użyj etykiet danych, aby wygodnie wyświetlać informacje dotyczące zmiennych, w tym tablic i struktur, podczas debugowania. Możesz również modyfikować wartości.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 432fd50d30347972d7b1fc8222a430fc90a9e590
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149966"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Wyświetlanie wartości danych we wskazówkach datapreview w edytorze kodu

Porady datapreview zapewniają wygodny sposób wyświetlania informacji o zmiennych w programie podczas debugowania. Etykietki danych działają tylko w trybie przerwania i są tylko w przypadku zmiennych, które znajdują się w bieżącym zakresie wykonywania. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="work-with-datatips"></a>Współpraca z etykietami danych

Etykietki danych są wyświetlane tylko w trybie przerwania i tylko dla zmiennych, które znajdują się w bieżącym zakresie wykonywania.

### <a name="display-a-datatip"></a>Wyświetlanie etykietki danych

1. Ustaw punkt przerwania w kodzie i Rozpocznij debugowanie, naciskając klawisz **F5** lub wybierając pozycję **Debuguj**  >  **Rozpocznij debugowanie**.

1. Po zatrzymaniu w punkcie przerwania Zatrzymaj wskaźnik myszy nad dowolną zmienną w bieżącym zakresie. Etykietki danych pojawia się, pokazując nazwę i bieżącą wartość zmiennej.

### <a name="make-a-datatip-transparent"></a>Ustaw etykietki danych jako przezroczysty

Aby uczynić etykietki danych przezroczystym w celu wyświetlenia kodu znajdującego się pod nim, w etykietki danych naciśnij klawisz **Ctrl**. Etykietki danych pozostaje przezroczysty, o ile przytrzymasz wciśnięty klawisz **Ctrl** . To nie działa w przypadku przypiętych lub zmiennoprzecinkowych etykiet danych.
### <a name="pin-a-datatip"></a>Przypinanie elementu etykietki danych

Aby przypiąć etykietki danych w taki sposób, aby pozostawał otwarty, wybierz ikonę Pinezka **do źródła** .

![Przypinanie elementu etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "Przypinanie elementu etykietki danych")

Przypiętą etykietki danych można przenieść, przeciągając ją wokół okna kodu. Ikona pinezki pojawia się na oprawie obok wiersza, do którego jest przypięty etykietki danych.

>[!NOTE]
>Etykietki danych są zawsze oceniane w kontekście, w którym wykonywanie jest wstrzymane, a nie z bieżącym kursorem lub lokalizacją etykietki danych. Jeśli umieścisz wskaźnik myszy nad zmienną w innej funkcji, która ma taką samą nazwę jak zmienna w bieżącym kontekście, zostanie wyświetlona wartość zmiennej w bieżącym kontekście.

### <a name="unpin-a-datatip-from-source"></a>Odepnij etykietki danych od źródła

Aby przestawić przypięty etykietki danych, umieść kursor nad etykietki danych i wybierz ikonę pinezki z menu kontekstowego.

Ikona pinezki zmieni się na przypiętą, a etykietki danych teraz zostanie przeciągnięta lub przeciągnięte nad wszystkie otwarte okna. Przestawne etykietki danych zamyka się po zakończeniu sesji debugowania.

### <a name="repin-a-datatip"></a>Przypiąć etykietki danych

Aby przypiąć zmiennoprzecinkową etykietki danych do źródła, umieść kursor nad nim w edytorze kodu i wybierz ikonę pinezki. Ikona pinezki zmieni się na przypiętą pozycję, a etykietki danych ponownie przypięto tylko do okna kod.

Jeśli etykietki danych jest przepływa nad oknem kodu nieźródłowym, ikona pinezki jest niedostępna, a etykietki danych nie może zostać przypięty. Aby uzyskać dostęp do ikony pinezki, zwróć etykietki danych do okna edytora kodu, przeciągając je lub dostarczając fokus okna kodu.

### <a name="close-a-datatip"></a>Zamknij etykietki danych

Aby zamknąć etykietki danych, umieść kursor nad etykietki danych i wybierz ikonę zamknięcia (**x**) z menu kontekstowego.

### <a name="close-all-datatips"></a>Zamknij wszystkie etykietki danych

Aby zamknąć wszystkie etykietki danych, w menu **Debuguj** wybierz polecenie **Wyczyść wszystkie etykietki** danych.

### <a name="close-all-datatips-for-a-specific-file"></a>Zamknij wszystkie etykietki danych dla określonego pliku

Aby zamknąć wszystkie etykietki danych dla określonego pliku, w menu **Debuguj** wybierz polecenie **Wyczyść wszystkie podpowiedzi danych przypięte \<Filename> do**.

## <a name="expand-and-edit-information"></a>Rozwiń i Edytuj informacje
Możesz użyć etykietek danych, aby rozwinąć tablicę, strukturę lub obiekt, aby wyświetlić jego elementy członkowskie. Możesz również edytować wartość zmiennej z etykietki danych.

### <a name="expand-a-variable"></a>Rozwiń zmienną

Aby rozwinąć obiekt w etykietki danych, aby wyświetlić jego elementy, umieść kursor nad strzałkami rozwiń przed nazwami elementów, aby wyświetlić elementy w formie drzewa. W przypadku przypiętej etykietki danych wybierz pole **+** przed nazwą zmiennej, a następnie rozwiń drzewo.

![Rozwiń element etykietki danych](../debugger/media/dbg-tour-data-tips.png "Rozwiń element etykietki danych")

Możesz użyć myszy lub klawiszy strzałek na klawiaturze, aby przejść w górę i w dół w rozwiniętym widoku.

Możesz również przypiąć rozwinięte elementy do przypiętej etykietki danych, umieszczając nad nimi kursor i wybierając ich ikony pinezki. Elementy są następnie wyświetlane w przypiętej etykietki danych po zwinięciu drzewa.

### <a name="edit-the-value-of-a-variable"></a>Edytowanie wartości zmiennej

Aby edytować wartość zmiennej lub elementu w etykietki danych, wybierz wartość, wpisz nową wartość i naciśnij klawisz **Enter**. Zaznaczenie jest wyłączone dla wartości tylko do odczytu.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Przypnij właściwości w etykietach danych

> [!NOTE]
> Ta funkcja jest obsługiwana w przypadku platformy .NET Core 3,0 lub nowszej.

Możesz szybko sprawdzić obiekty według ich właściwości w etykietkach danych za pomocą narzędzia **Pinnable Properties** .  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz ikonę pinezki, która jest wyświetlana, lub kliknij prawym przyciskiem myszy i wybierz opcję **Przypnij element członkowski jako ulubiony** w menu kontekstowym.  Powoduje to odfiltrowanie tej właściwości do górnej części listy właściwości obiektu, a nazwa właściwości i wartość są wyświetlane w prawej kolumnie etykietki danych.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję **Odepnij członka jako ulubioną** w menu kontekstowym.

![Przypinanie właściwości w etykietki danych](../debugger/media/basic-pin-datatip.gif "Przypinanie właściwości w etykietki danych")

Można również przełączać nazwy właściwości i odfiltrować przypięte właściwości podczas wyświetlania listy właściwości obiektu w etykietki danych.  Możesz uzyskać dostęp do dowolnej opcji, klikając prawym przyciskiem myszy wiersz zawierający właściwość i wybierając pozycję **Pokaż tylko przypiętych członków** lub **Ukryj nazwy przypiętych elementów członkowskich w** opcjach wartości w menu kontekstowym.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Wizualizowanie złożonych typów danych

Ikona lupy obok zmiennej lub elementu w etykietki danych oznacza, że co najmniej jeden [wizualizator](../debugger/create-custom-visualizers-of-data.md), taki jak [wizualizator tekstu](../debugger/string-visualizer-dialog-box.md), jest dostępny dla zmiennej. Wizualizatory wyświetlają informacje bardziej zrozumiałe, czasami graficzne, sposób.

Aby wyświetlić element przy użyciu domyślnego wizualizatora dla typu danych, wybierz ikonę lupy ikona ![wizualizatora](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora"). Wybierz strzałkę obok ikony lupy, aby wybrać z listy wizualizatorów dla typu danych.

## <a name="add-a-variable-to-a-watch-window"></a>Dodawanie zmiennej do okno wyrażeń kontrolnych

Jeśli chcesz kontynuować obserwację zmiennej, możesz dodać ją do okna **czujki** z etykietki danych. Kliknij prawym przyciskiem myszy zmienną w etykietki danych, a następnie wybierz polecenie **Dodaj czujkę**.

Zmienna pojawia się w oknie **czujka** . Jeśli wersja programu Visual Studio obsługuje więcej niż jedno okno **czujki** , zmienna pojawia się w **zegarku 1**.

## <a name="import-and-export-datatips"></a>Importuj i Eksportuj etykietki danych

Można eksportować etykietki danych do pliku XML, który można udostępniać lub edytować za pomocą edytora tekstu. Można również zaimportować plik XML etykietki danych, który został odebrany lub zmodyfikowany.

**Aby wyeksportować etykietki danych:**

1. Wybierz kolejno opcje **Debuguj**  >  **eksport** danych.

1. W oknie dialogowym **Eksportuj etykietki** danych przejdź do lokalizacji, w której ma zostać zapisany plik XML, wpisz nazwę pliku, a następnie wybierz pozycję **Zapisz**.

**Aby zaimportować etykietki danych:**

1. Wybierz pozycję **Debuguj**  >  **Importuj etykietki** danych.

1. W oknie dialogowym **Importuj porady dotyczące** danych wybierz plik XML z danymi, które chcesz otworzyć, a następnie wybierz pozycję **Otwórz**.

## <a name="see-also"></a>Zobacz także
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
