---
title: Okno właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662074"
---
# <a name="properties-window"></a>Okno Właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno służy do wyświetlania i zmieniania właściwości czasu projektowania oraz zdarzeń wybranych obiektów, które znajdują się w edytorach i projektantach. Można również użyć okna **Właściwości** do edytowania i wyświetlania właściwości plików, projektów i rozwiązań. Okno **Właściwości** można znaleźć w menu **Widok** . Można go również otworzyć, naciskając klawisz F4 lub wpisując **Właściwości** w oknie **Szybkie uruchamianie** .

 W oknie **Właściwości** są wyświetlane różne typy pól edycji, w zależności od potrzeb konkretnej właściwości. Te pola edycji obejmują pola edycji, listy rozwijane i linki do okien dialogowych edytorów niestandardowych. Właściwości oznaczone kolorem szarym są tylko do odczytu.

## <a name="uielement-list"></a>Lista elementów UI
 Nazwa obiektu wyświetla listę aktualnie zaznaczonego obiektu lub obiektów. Widoczne są tylko obiekty z aktywnego edytora lub projektanta. Po zaznaczeniu wielu obiektów pojawiają się tylko właściwości wspólne dla wszystkich wybranych obiektów.

 Kategoryzacja wyświetla wszystkie właściwości i wartości właściwości dla wybranego obiektu według kategorii. Możesz zwinąć kategorię, aby zmniejszyć liczbę widocznych właściwości. Po rozwinięciu lub zwinięciu kategorii zobaczysz znak plus (+) lub minus (-) z lewej strony nazwy kategorii. Kategorie są wyświetlane alfabetycznie.

 Alfabetyczne alfabetycznie sortuje wszystkie właściwości i zdarzenia czasu projektowania dla wybranych obiektów. Aby edytować Właściwość niewyszarzoną, kliknij w komórce po prawej stronie i wprowadź zmiany.

 Na stronach właściwości jest wyświetlane okno dialogowe **strony właściwości** lub **Projektant projektu** dla wybranego elementu. Na stronach właściwości jest wyświetlany podzestaw, taki sam lub nadzbiór właściwości dostępnych w oknie **Właściwości** . Ten przycisk służy do wyświetlania i edytowania właściwości związanych z aktywną konfiguracją projektu.

 Właściwości wyświetla właściwości obiektu. Wiele obiektów ma także zdarzenia, które można wyświetlić za pomocą okna **Właściwości** .

 Sortuj wg właściwości grupy źródłowej właściwości według źródła, takie jak dziedziczenie, zastosowane style i powiązania. Dostępne tylko podczas edytowania plików XAML w projektancie.

 Zdarzenia wyświetla zdarzenia dla obiektu.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy formularz lub Projektant formantów jest aktywny w kontekście [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektu. Podczas edytowania plików XAML zdarzenia są wyświetlane na osobnej karcie okna właściwości.

 Komunikaty wyświetla wszystkie komunikaty systemu Windows. Umożliwia dodawanie lub usuwanie określonych funkcji programu obsługi dla komunikatów dostarczonych dla wybranej klasy.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy **Widok klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektu.

 Zastąpień wyświetla wszystkie funkcje wirtualne dla wybranej klasy i umożliwia dodawanie lub usuwanie zastąpień funkcji.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** jest dostępny tylko wtedy, gdy **Widok klasy** jest aktywnym oknem w kontekście [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektu.

 W okienku opis jest wyświetlany typ właściwości i Krótki opis właściwości. Można wyłączyć opis właściwości i przy użyciu polecenia Description w menu skrótów.

> [!NOTE]
> Ten formant paska narzędzi okna **Właściwości** nie jest dostępny podczas EDYTOWANIA plików XAML w projektancie.

 Widok miniatury przedstawia wizualną reprezentację aktualnie wybranego elementu podczas edycji plików XAML w projektancie.

 Funkcja wyszukiwania udostępnia funkcję wyszukiwania dla właściwości i zdarzeń podczas edytowania plików XAML w projektancie. Pole wyszukiwania reaguje na wyszukiwanie częściowe wyrazów i aktualizuje wyniki wyszukiwania podczas wpisywania.

## <a name="see-also"></a>Zobacz też
 [Odwołania do właściwości projektu](../../ide/reference/project-properties-reference.md) [Dostosowywanie układów okna](../../ide/customizing-window-layouts-in-visual-studio.md)
