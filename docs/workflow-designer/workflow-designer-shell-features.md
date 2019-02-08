---
title: Funkcje powłoki Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4519be8ec5c5d4ba8a611df1880ae770a83cf981
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919472"
---
# <a name="workflow-designer-shell-features"></a>Funkcje powłoki Projektanta przepływu pracy

Projektant przepływu pracy składa się z trzech głównych obszarach interfejsu użytkownika: powierzchni projektanta i nad nim za pomocą paska nawigacji powłoki poniżej. Na pasku nawigacji, umieszczony w górnej części ekranu służy do wyświetlania listy elementów nadrzędnych bieżącego działania głównego. Aby uzyskać więcej informacji, zobacz [jak: Użyj do stron nadrzędnych](../workflow-designer/how-to-use-breadcrumb-navigation.md). Powierzchni projektanta umieszczony na środku ekranu jest używana do tworzenia przepływów pracy. Powłoka, umieszczony w dolnej części ekranu zawiera szereg przyciski umożliwiające zarządzanie bieżącym widokiem.

## <a name="shell-features"></a>Funkcje powłoki
 Powłoka zawiera przyciski po prawej stronie paska, który umożliwia powiększanie lub pomniejszanie przepływu pracy, do zawartości przepływu pracy do rozmiaru ekranu i Pokaż lub Ukryj mapowanie przeglądów. Użytkownik może również powiększyć lub pomniejszyć, przepływ pracy za pomocą skrótów klawiaturowych CTRL ++ i CTRL +-.

## <a name="overview-map"></a>Mapowanie przeglądów
 Mapowanie przeglądów wyświetla małą wersję działanie całej głównym bieżącego łączy do stron nadrzędnych, w tym wszystkie jego elementy podrzędne i wszystkie rozwinięte dzieci. Ma okienka ekranu, prostokąt z obramowaniem pomarańczowego, które przedstawia część działania aktualnie wyświetlany w edytorze. Przeciągnięcie prostokąt wokół mapowanie przeglądów Przewija projektanta przepływów pracy i zmiany widoku edytora.

> [!NOTE]
> Jest Zwirtualizowana interfejsu użytkownika projektanta przepływu pracy. Projektanci działań są renderowane tylko wtedy, gdy jest to wymagane. Jeśli nigdy nie został wystawiony przez część przepływu pracy na powierzchni projektowej, część pojawia się jako białe na mapie Przegląd. Przewijanie wokół mapowanie przeglądów całkowicie rysuje przepływu pracy.

## <a name="copying-or-saving-workflows-as-images"></a>Kopiowanie lub zapisywanie przepływów pracy jako obrazów
 Przepływy pracy można skopiować format mapy bitowej lub zapisane w formacie mapy bitowej lub wektora. Kopiowanie lub zapisywanie obrazu umożliwia eksportowanie widoku całej aktywności głównym bieżącego łączy do stron nadrzędnych, w tym wszystkie jego elementy podrzędne i wszystkie rozwinięte dzieci do innego programu.

 Aby skopiować jako obraz, kliknij prawym przyciskiem myszy projektanta i wybierz pozycję **Kopiuj jako obraz**. Aby zapisać jako obraz, kliknij prawym przyciskiem myszy projektanta i wybierz pozycję **Zapisz jako obraz**. Przepływy pracy można zapisać w formacie JPG, PNG, GIF lub XPS. Wybrano format **Zapisz jako** okno dialogowe w **Zapisz jako typ:** listy rozwijanej listy w dolnej części okna.

## <a name="fonts-and-colors"></a>Czcionki i kolory

Czcionki używane w Projektancie przepływu pracy w programie Visual Studio są kontrolowane przez czcionka środowiska. Zmieniają się kolory, wyświetlana w Projektancie przepływu pracy, korzystając z dużego kontrastu schemat kolorów dla motywu systemu operacyjnego. Po wprowadzeniu zmian w ustawieniach czcionek i kolorów, aby zmiany zostały wprowadzone w Projektancie przepływu pracy, należy ponownie uruchomić program Visual Studio.