---
title: Okno Właściwości
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 1302b2e035bc884bd6b3e914b848eada79e45236
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014994"
---
# <a name="properties-window"></a>Okno Właściwości
To okno służy do wyświetlania i zmieniania właściwości projektowania oraz zdarzeń zaznaczonych obiektów, które znajdują się w edytorach i projektantach. Można również użyć **właściwości** okna do edytowania i wyświetlania plików, projekt i właściwości rozwiązania. Możesz znaleźć **właściwości** okno na **widoku** menu. Możesz też go otworzyć, naciskając klawisz F4 lub wpisując **właściwości** w **Szybkie uruchamianie** okna.

 **Właściwości** oknie zostaną wyświetlone różne typy pól edycji, w zależności od potrzeb danej właściwości. Edytuj te pola zawierają pola tekstowe, listy rozwijane i łącza do niestandardowego edytora okien dialogowych. Właściwości zaznaczone na szaro są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI
 Nazwa obiektu

 Wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z aktywnego edytora lub projektanta. Po zaznaczeniu wielu obiektów są wyświetlane tylko właściwości wspólne dla wszystkich wybranych obiektów.

 Dzielony na kategorie

 Wyświetla listę wszystkich właściwości i wartości właściwości dla wybranego obiektu, według kategorii. Można zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Po rozwinięciu lub zwinięciu kategorii wyświetlany jest plus (+) lub minus (-) z lewej strony nazwy kategorii. Kategorie są wymieniane alfabetycznie.

 Alfabetyczne

 Sortuje alfabetycznie wszystkie właściwości projektowania i zdarzenia dla wybranych obiektów. Aby edytować niewygaszoną właściwość, kliknij w komórce po jego prawej stronie, a następnie wprowadź zmiany.

 Strony właściwości

 Wyświetla **stron właściwości** okno dialogowe lub **projektanta projektu** dla wybranego elementu. Strony właściwości wyświetla podzbiór, taki sam lub nadzbiór właściwości dostępnych w **właściwości** okna. Ten przycisk służy do wyświetlania i edytowania właściwości powiązanych z aktywnej konfiguracji projektu.

 Właściwości

 Wyświetla właściwości dla obiektu. Wiele obiektów ma także zdarzenia, które mogą być wyświetlane za pomocą **właściwości** okna.

 Sortuj według źródła właściwości

 Grupuje właściwości według źródła, takiego jak dziedziczenie, zastosowanie style i powiązania. Dostępna tylko podczas edytowania plików XAML w projektancie.

 Zdarzenia

 Wyświetla zdarzenia dla obiektu.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna tylko jest dostępna, gdy formularz lub Projektant formantów jest aktywny w kontekście [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Podczas edycji plików XAML, zdarzenia są wyświetlane na osobnej karcie okna właściwości.


 Komunikaty

 Wyświetla listę wszystkich komunikatów Windows. Umożliwia dodawanie lub usuwanie funkcji obsługi dla wiadomości przewidzianych dla wybranej klasy.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna jest dostępna tylko podczas **Widok klas** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Overrides

 Wyświetla listę wszystkich funkcji wirtualnych dla wybranej klasy i pozwala na dodawanie i usuwanie funkcji nadrzędnych.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna jest dostępna tylko podczas **Widok klas** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.


 Okienko opisu

 Pokazuje typ właściwości i krótki opis właściwości. Możesz wyłączyć opis właściwości i Włącz za pomocą polecenia opis w menu skrótów.

> [!NOTE]
> To **właściwości** formant paska narzędzi okna nie jest dostępna podczas edycji plików XAML w projektancie.


 Widok miniatur

 Pokazuje graficzną reprezentację obecnie wybranego elementu podczas edycji plików XAML w projektancie.

 Wyszukaj

 Zawiera funkcję wyszukiwania dla właściwości i zdarzenia podczas edycji plików XAML w projektancie. Pole wyszukiwania reaguje na wyszukiwanie wyrazów częściowych i aktualizuje wyniki wyszukiwania podczas wpisywania.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)