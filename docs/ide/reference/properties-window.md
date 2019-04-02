---
title: Okno Właściwości
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e26bd9d874ba5526a858e32907bff6676b68c81e
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790735"
---
# <a name="properties-window"></a>Okno właściwości

To okno służy do wyświetlania i zmieniania właściwości projektowania oraz zdarzeń zaznaczonych obiektów, które znajdują się w edytorach i projektantach. Można również użyć **właściwości** okna do edytowania i wyświetlania plików, projekt i właściwości rozwiązania. Możesz znaleźć **właściwości** okno na **widoku** menu. Można go również otworzyć, naciskając klawisz **F4** lub wpisując **właściwości** w polu wyszukiwania.

**Właściwości** oknie zostaną wyświetlone różne typy pól edycji, w zależności od potrzeb danej właściwości. Edytuj te pola zawierają pola tekstowe, listy rozwijane i łącza do niestandardowego edytora okien dialogowych. Właściwości zaznaczone na szaro są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI

Obiekt name\
Wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z aktywnego edytora lub projektanta. Po zaznaczeniu wielu obiektów są wyświetlane tylko właściwości wspólne dla wszystkich wybranych obiektów.

Categorized\
Wyświetla listę wszystkich właściwości i wartości właściwości dla wybranego obiektu, według kategorii. Można zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Po rozwinięciu lub zwinięciu kategorii wyświetlany jest plus (+) lub minus (-) z lewej strony nazwy kategorii. Kategorie są wymieniane alfabetycznie.

Alphabetical\
Sortuje alfabetycznie wszystkie właściwości projektowania i zdarzenia dla wybranych obiektów. Aby edytować niewygaszoną właściwość, kliknij w komórce po jego prawej stronie, a następnie wprowadź zmiany.

Właściwość Pages\
Wyświetla **stron właściwości** okno dialogowe lub **projektanta projektu** dla wybranego elementu. Strony właściwości wyświetla podzbiór, taki sam lub nadzbiór właściwości dostępnych w **właściwości** okna. Ten przycisk służy do wyświetlania i edytowania właściwości powiązanych z aktywnej konfiguracji projektu.

Properties\
Wyświetla właściwości dla obiektu. Wiele obiektów ma także zdarzenia, które mogą być wyświetlane za pomocą **właściwości** okna.

Sortuj według Source\ właściwości
Grupuje właściwości według źródła, takiego jak dziedziczenie, zastosowanie style i powiązania. Dostępna tylko podczas edytowania plików XAML w projektancie.

Events\
Wyświetla zdarzenia dla obiektu.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna tylko jest dostępna, gdy formularz lub Projektant formantów jest aktywny w kontekście [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Podczas edycji plików XAML, zdarzenia są wyświetlane na osobnej karcie okna właściwości.

Messages\
Wyświetla listę wszystkich komunikatów Windows. Umożliwia dodawanie lub usuwanie funkcji obsługi dla wiadomości przewidzianych dla wybranej klasy.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna jest dostępna tylko podczas **Widok klas** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Overrides\
Wyświetla listę wszystkich funkcji wirtualnych dla wybranej klasy i pozwala na dodawanie i usuwanie funkcji nadrzędnych.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna jest dostępna tylko podczas **Widok klas** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Opis pane\
Pokazuje typ właściwości i krótki opis właściwości. Możesz wyłączyć opis właściwości i Włącz za pomocą polecenia opis w menu skrótów.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna nie jest dostępna podczas edycji plików XAML w projektancie.

View\ miniatury
Pokazuje graficzną reprezentację obecnie wybranego elementu podczas edycji plików XAML w projektancie.

Search\
Zawiera funkcję wyszukiwania dla właściwości i zdarzenia podczas edycji plików XAML w projektancie. Pole wyszukiwania reaguje na wyszukiwanie wyrazów częściowych i aktualizuje wyniki wyszukiwania podczas wpisywania.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)