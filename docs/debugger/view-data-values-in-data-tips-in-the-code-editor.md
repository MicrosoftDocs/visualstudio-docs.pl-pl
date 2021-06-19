---
title: Wyświetlanie wartości zmiennych w etykietkach | Microsoft Docs
description: Użyj etykietek danych, aby wygodnie wyświetlać informacje o zmiennych, w tym tablice i struktury, podczas debugowania. Można również modyfikować wartości.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a84c3379c04799aa1faea5b0e62afe0ef1aa11e9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386478"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Wyświetlanie wartości danych w etykietkach danych w edytorze kodu

Etykietki danych zapewniają wygodny sposób wyświetlania informacji o zmiennych w programie podczas debugowania. Etykietki danych działają tylko w trybie przerwania i tylko ze zmiennymi, które znajdują się w bieżącym zakresie wykonywania. Jeśli po raz pierwszy próbujesz debugować kod, przed rozpoczęciem [](../debugger/debugging-absolute-beginners.md) pracy z [](../debugger/write-better-code-with-visual-studio.md) tym artykułem warto przeczytać artykuł Debugowanie dla bezwzględnych początkujących oraz Techniki i narzędzia debugowania.

## <a name="work-with-datatips"></a>Praca z etykietkami danych

Etykietki danych są wyświetlane tylko w trybie przerwania i tylko w zmiennych, które znajdują się w bieżącym zakresie wykonywania.

### <a name="display-a-datatip"></a>Wyświetlanie etykietki danych

1. Ustaw punkt przerwania w kodzie i rozpocznij debugowanie, naciskając **klawisz F5** lub wybierając **pozycję Debuguj**  >  **rozpocznij debugowanie.**

1. Po wstrzymaniu w punkcie przerwania umieść kursor na dowolnej zmiennej w bieżącym zakresie. Zostanie wyświetlona etykietka danych z nazwą i bieżącą wartością zmiennej.

### <a name="make-a-datatip-transparent"></a>Przezroczystość etykietki danych

Aby sprawić, aby etykietka danych była przezroczysta, aby zobaczyć kod, który znajduje się poniżej, w etykietce danych naciśnij **klawisze Ctrl**. Etykietka danych pozostaje niewidoczna, o ile przytrzymasz naciśnięty **klawisz Ctrl.** Nie działa to w przypadku przypiętych lub przestawnych etykietek danych.
### <a name="pin-a-datatip"></a>Przypinanie etykietki danych

Aby przypiąć etykietkę danych tak, aby była otwarta, wybierz ikonę pinezki **Przypnij do źródła.**

![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "Przypinanie etykietki danych")

Przypiętą etykietkę danych można przenieść, przeciągając ją w oknie kodu. Ikona pinezki jest wyświetlana w rynnie obok wiersza, do których jest przypięta etykietka danych.

>[!NOTE]
>Etykietki danych są zawsze oceniane w kontekście, w którym wstrzymano wykonywanie, a nie bieżącego kursora ani lokalizacji etykietki danych. Jeśli najedziesz kursorem na zmienną w innej funkcji, która ma taką samą nazwę jak zmienna w bieżącym kontekście, zostanie wyświetlona wartość zmiennej w bieżącym kontekście.

### <a name="unpin-a-datatip-from-source"></a>Odpinanie etykietki danych od źródła

Aby przesłonić przypiętą etykietkę danych, umieść kursor nad etykietką danych i wybierz ikonę pinezki z menu kontekstowego.

Ikona pinezki zmienia się na odpiętą pozycję, a etykietka danych jest teraz wyświetlana jako zmiennoprzecinkowa lub można ją przeciągać nad wszystkimi otwartymi oknami. Przestawne etykietki danych są zamykane po zakończeniu sesji debugowania.

### <a name="repin-a-datatip"></a>Ponowne przypinanie etykietki danych

Aby odpiąć przestawną etykietkę danych do źródła, umieść kursor nad nim w edytorze kodu i wybierz ikonę pinezki. Ikona pinezki zmieni się na przypiętą pozycję, a etykietka danych zostanie ponownie przypięta tylko do okna kodu.

Jeśli etykietka danych jest przestawna w oknie kodu nie źródłowego, ikona pinezki jest niedostępna i nie można ponownie przypiąć etykietki danych. Aby uzyskać dostęp do ikony pinezki, zwróć etykietkę danych do okna edytora kodu, przeciągając ją lub nadając fokus okna kodu.

### <a name="close-a-datatip"></a>Zamykanie etykietki danych

Aby zamknąć etykietkę danych, umieść kursor nad etykietką danych i wybierz ikonę zamknięcia **(x**) z menu kontekstowego.

### <a name="close-all-datatips"></a>Zamknij wszystkie etykietki danych

Aby zamknąć wszystkie etykietki danych, w menu **Debugowanie** wybierz pozycję **Wyczyść wszystkie etykietki danych.**

### <a name="close-all-datatips-for-a-specific-file"></a>Zamknij wszystkie etykietki danych dla określonego pliku

Aby zamknąć wszystkie etykietki danych dla określonego pliku, w menu **Debugowanie** wybierz pozycję Wyczyść wszystkie **etykietki \<Filename> danych przypięte do elementu**.

## <a name="expand-and-edit-information"></a>Rozwijanie i edytowanie informacji
Możesz użyć etykietek danych, aby rozwinąć tablicę, strukturę lub obiekt, aby wyświetlić jego elementy członkowskie. Możesz również edytować wartość zmiennej z etykietki danych.

### <a name="expand-a-variable"></a>Rozwijanie zmiennej

Aby rozwinąć obiekt w etykietce danych, aby wyświetlić jego elementy, umieść kursor nad strzałkami rozwijania przed nazwami elementów, aby wyświetlić elementy w postaci drzewa. W przypadku przypiętej etykietki danych wybierz wartość przed nazwą zmiennej, a **+** następnie rozwiń drzewo.

![Rozwijanie etykietki danych](../debugger/media/dbg-tour-data-tips.png "Rozwijanie etykietki danych")

Możesz użyć myszy lub klawiszy strzałek na klawiaturze, aby poruszać się w górę i w dół w widoku rozwiniętym.

Możesz również przypiąć rozwinięte elementy do przypiętej etykietki danych, umieszczając na nich kursor i wybierając ich ikony pinezki. Elementy są następnie wyświetlane w przypiętej etykietce danych po zwiniętym drzewie.

### <a name="edit-the-value-of-a-variable"></a>Edytowanie wartości zmiennej

Aby edytować wartość zmiennej lub elementu w etykietce danych, wybierz wartość, wpisz nową wartość i naciśnij **klawisz Enter**. Wybór jest wyłączony dla wartości tylko do odczytu.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Przypinanie właściwości w etykietkach danych

> [!NOTE]
> Ta funkcja jest obsługiwana w przypadku platform .NET Core 3.0 lub wyższych.

Za pomocą narzędzia **Pinnable Properties** można szybko sprawdzać obiekty według ich właściwości w etykietkach danych.  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz wyświetloną ikonę pinezki lub kliknij prawym przyciskiem myszy i wybierz opcję Przypnij element **członkowski** jako ulubiony w wynikowym menu kontekstowym.  Ta właściwość jest wyświetlana na początku listy właściwości obiektu, a nazwa i wartość właściwości są wyświetlane w prawej kolumnie etykietki danych.  Aby odpiąć właściwość, ponownie wybierz ikonę pinezki lub wybierz opcję Odepnij element **członkowski** jako ulubiony w menu kontekstowym.

![Przypinanie właściwości w etykietce danych](../debugger/media/basic-pin-datatip.gif "Przypinanie właściwości w etykietce danych")

Podczas wyświetlania listy właściwości obiektu w etykietce danych można również przełączać nazwy właściwości i filtrować nie przypięte właściwości.  Dostęp do każdej opcji można uzyskać, klikając prawym  przyciskiem myszy wiersz  zawierający właściwość i wybierając z menu kontekstowego opcję Pokaż tylko przypięte elementy członkowskie lub Ukryj przypięte nazwy elementów członkowskich w wartościach.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Wizualizowanie złożonych typów danych

Ikona lupy obok zmiennej lub elementu w etykietce danych [oznacza,](../debugger/create-custom-visualizers-of-data.md)że dla [](../debugger/string-visualizer-dialog-box.md)zmiennej jest dostępny co najmniej jeden wizualizator , taki jak wizualizator tekstu. Wizualizatorzy wyświetlają informacje w bardziej zrozumiały, czasami graficzny sposób.

Aby wyświetlić element przy użyciu domyślnego wizualizatora dla typu danych, wybierz ikonę ![lupy Ikona wizualizatora](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora"). Wybierz strzałkę obok ikony lupy, aby wybrać z listy wizualizatorów dla typu danych.

## <a name="add-a-variable-to-a-watch-window"></a>Dodawanie zmiennej do okno wyrażeń kontrolnych

Jeśli chcesz kontynuować obserwowanie zmiennej, możesz dodać ją do okna **Obserwowanie** z etykietki danych. Kliknij prawym przyciskiem myszy zmienną w etykietce danych, a następnie wybierz pozycję **Dodaj czujkę.**

Zmienna zostanie wyświetlona w **oknie Czujka.** Jeśli Twoja Visual Studio obsługuje więcej niż jedno **okno Czujka,** zmienna pojawia się w **zegarku Watch 1.**

## <a name="import-and-export-datatips"></a>Importowanie i eksportowanie etykietek danych

Etykietki danych można wyeksportować do pliku XML, który można udostępniać lub edytować za pomocą edytora tekstów. Możesz również zaimportować otrzymany lub edytowany plik XML etykietki danych.

**Aby wyeksportować etykietki danych:**

1. Wybierz **pozycję**  >  **Debuguj eksportuj etykietki danych.**

1. W **oknie dialogowym Eksportowanie** etykietek danych przejdź do lokalizacji, w którym chcesz zapisać plik XML, wpisz nazwę pliku, a następnie wybierz pozycję **Zapisz.**

**Aby zaimportować etykietki danych:**

1. Wybierz **pozycję**  >  **Debuguj etykietki danych importu.**

1. W **oknie dialogowym Import DataTips** (Importowanie etykietek danych) wybierz plik XML DataTips, który chcesz otworzyć, a następnie wybierz pozycję **Open (Otwórz).**

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
