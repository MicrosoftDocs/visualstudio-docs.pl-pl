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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1be1d4fa9f1b088547bb21dfb64254209783d7e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565711"
---
# <a name="properties-window"></a>Okno właściwości

To okno służy do wyświetlania i zmieniania właściwości i zdarzeń czasu projektowania wybranych obiektów znajdujących się w edytorach i projektantach. Można również użyć okna **Właściwości** do edycji i wyświetlania plików, projektu i właściwości rozwiązania. Okno **Właściwości** można znaleźć w menu **Widok.** Można go również otworzyć, naciskając **klawisz F4** lub wpisując **polecenie Właściwości** w polu wyszukiwania.

Okno **Właściwości** wyświetla różne typy pól edycji, w zależności od potrzeb określonej właściwości. Te pola edycji obejmują pola edycji, listy rozwijane i łącza do okien dialogowych edytora niestandardowego. Właściwości wyświetlane na szaro są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI

Nazwa obiektu\
Wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z aktywnego edytora lub projektanta. Po zaznaczeniu wielu obiektów wyświetlane są tylko właściwości wspólne dla wszystkich zaznaczonych obiektów.

Kategoryzowane\
Wyświetla listę wszystkich właściwości i wartości właściwości dla wybranego obiektu według kategorii. Można zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Po rozwinięciu lub zwinięciu kategorii po lewej stronie nazwy kategorii jest widoczny plus (+) lub minus (-). Kategorie są wyświetlane alfabetycznie.

Alfabetycznie\
Alfabetycznie sortuje wszystkie właściwości czasu projektowania i zdarzenia dla wybranych obiektów. Aby edytować nieprzyciemnioną właściwość, kliknij komórkę po prawej stronie i wprowadź zmiany.

Strony właściwości\
Wyświetla okno dialogowe **Strony właściwości** lub **Projektant projektu** dla wybranego elementu. Strony właściwości wyświetla podzbiór, ten sam lub nadzbiór właściwości dostępnych w oknie **Właściwości.** Ten przycisk służy do wyświetlania i edytowania właściwości związanych z aktywną konfiguracją projektu.

Właściwości\
Wyświetla właściwości obiektu. Wiele obiektów ma również zdarzenia, które można przeglądać za pomocą okna **Właściwości.**

Sortuj według źródła właściwości\
Grupuje właściwości według źródła, takie jak dziedziczenie, zastosowane style i powiązania. Dostępne tylko podczas edytowania plików XAML w projektancie.

Wydarzenia\
Wyświetla zdarzenia dla obiektu.

> [!NOTE]
> Ten **formant** paska narzędzi okna właściwości jest dostępny tylko wtedy, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] gdy projektant formularzy lub formantów jest aktywny w kontekście projektu. Podczas edytowania plików XAML zdarzenia są wyświetlane na osobnej karcie okna właściwości.

Wiadomości\
Wyświetla listę wszystkich komunikatów systemu Windows. Umożliwia dodawanie lub usuwanie określonych funkcji obsługi dla komunikatów dostarczonych dla wybranej klasy.

> [!NOTE]
> Ten **formant** paska narzędzi okna Właściwości jest dostępny tylko wtedy, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] gdy widok **klasy** jest aktywnym oknem w kontekście projektu.

Zastąpienia\
Wyświetla listę wszystkich funkcji wirtualnych dla wybranej klasy i umożliwia dodawanie lub usuwanie nadrzędnych funkcji.

> [!NOTE]
> Ten **formant** paska narzędzi okna Właściwości jest dostępny tylko wtedy, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] gdy widok **klasy** jest aktywnym oknem w kontekście projektu.

Okienko Opis\
Pokazuje typ właściwości i krótki opis właściwości. Opis właściwości można wyłączyć i włączyć za pomocą polecenia Opis w menu skrótów.

> [!NOTE]
> Ten **formant** paska narzędzi okna Właściwości nie jest dostępny podczas edytowania plików XAML w projektancie.

Widok miniatur\
Pokazuje wizualną reprezentację aktualnie wybranego elementu podczas edytowania plików XAML w projektancie.

Szukaj\
Udostępnia funkcję wyszukiwania właściwości i zdarzeń podczas edytowania plików XAML w projektancie. Pole wyszukiwania odpowiada na częściowe wyszukiwanie wyrazów i aktualizuje wyniki wyszukiwania podczas pisania.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
