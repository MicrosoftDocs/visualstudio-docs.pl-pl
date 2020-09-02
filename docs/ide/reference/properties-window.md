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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565711"
---
# <a name="properties-window"></a>Okno właściwości

To okno służy do wyświetlania i zmieniania właściwości czasu projektowania oraz zdarzeń wybranych obiektów, które znajdują się w edytorach i projektantach. Można również użyć okna **Właściwości** do edytowania i wyświetlania właściwości plików, projektów i rozwiązań. Okno **Właściwości** można znaleźć w menu **Widok** . Można go również otworzyć, naciskając klawisz **F4** lub wpisując **Właściwości** w polu wyszukiwania.

W oknie **Właściwości** są wyświetlane różne typy pól edycji, w zależności od potrzeb konkretnej właściwości. Te pola edycji obejmują pola edycji, listy rozwijane i linki do okien dialogowych edytorów niestandardowych. Właściwości oznaczone kolorem szarym są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI

Nazwa obiektu \
Wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z aktywnego edytora lub projektanta. Po zaznaczeniu wielu obiektów pojawiają się tylko właściwości wspólne dla wszystkich wybranych obiektów.

Skategoryzowane
Wyświetla wszystkie właściwości i wartości właściwości dla wybranego obiektu według kategorii. Możesz zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Po rozwinięciu lub zwinięciu kategorii zobaczysz znak plus (+) lub minus (-) z lewej strony nazwy kategorii. Kategorie są wyświetlane alfabetycznie.

Alfabetycznej
Alfabetycznie sortuje wszystkie właściwości czasu projektowania i zdarzenia dla wybranych obiektów. Aby edytować Właściwość niewyszarzoną, kliknij w komórce po prawej stronie i wprowadź zmiany.

Strony właściwości \
Wyświetla okno dialogowe **strony właściwości** lub **Projektant projektu** dla wybranego elementu. Na stronach właściwości jest wyświetlany podzestaw, taki sam lub nadzbiór właściwości dostępnych w oknie **Właściwości** . Ten przycisk służy do wyświetlania i edytowania właściwości związanych z aktywną konfiguracją projektu.

Aœciwoœci
Wyświetla właściwości obiektu. Wiele obiektów ma także zdarzenia, które można wyświetlić za pomocą okna **Właściwości** .

Sortuj według źródła właściwości \
Grupuje właściwości według źródła, takie jak dziedziczenie, zastosowane style i powiązania. Dostępne tylko podczas edytowania plików XAML w projektancie.

Wydarzeniach
Wyświetla zdarzenia dla obiektu.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy formularz lub Projektant formantów jest aktywny w kontekście [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu. Podczas edytowania plików XAML zdarzenia są wyświetlane na osobnej karcie okna właściwości.

Komunikaty
Wyświetla listę wszystkich komunikatów systemu Windows. Umożliwia dodawanie lub usuwanie określonych funkcji programu obsługi dla komunikatów dostarczonych dla wybranej klasy.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy **Widok klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Powoduje
Wyświetla wszystkie funkcje wirtualne dla wybranej klasy i umożliwia dodawanie lub usuwanie funkcji przesłaniania.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy **Widok klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu.

Okienko opisu \
Pokazuje typ właściwości i Krótki opis właściwości. Można wyłączyć opis właściwości i przy użyciu polecenia Description w menu skrótów.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** nie jest dostępny podczas EDYTOWANIA plików XAML w projektancie.

Widok miniatur \
Pokazuje wizualną reprezentację aktualnie wybranego elementu podczas edycji plików XAML w projektancie.

Wyszukiwania
Udostępnia funkcję wyszukiwania dla właściwości i zdarzeń podczas edytowania plików XAML w projektancie. Pole wyszukiwania reaguje na wyszukiwanie częściowe wyrazów i aktualizuje wyniki wyszukiwania podczas wpisywania.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
