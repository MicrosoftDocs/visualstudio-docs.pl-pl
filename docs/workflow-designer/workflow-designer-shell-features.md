---
title: Funkcje powłoki Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c57beeec6859e9346953fd8047410200187a026f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649733"
---
# <a name="workflow-designer-shell-features"></a>Funkcje powłoki Projektanta przepływu pracy

Projektant przepływu pracy składa się z trzech głównych obszarów interfejsu użytkownika: powierzchni projektanta, paska nawigacyjnego powyżej oraz powłoki poniżej. Pasek nawigacyjny, umieszczony w górnej części ekranu, służy do wyświetlania listy elementów nadrzędnych bieżącego działania głównego. Aby uzyskać więcej informacji, zobacz [How to: Use the webnawigacji](../workflow-designer/how-to-use-breadcrumb-navigation.md). Powierzchnia projektanta umieszczona na środku ekranu służy do tworzenia przepływów pracy. Powłoka umieszczona w dolnej części ekranu zawiera kilka przycisków służących do zarządzania bieżącym widokiem.

## <a name="shell-features"></a>Funkcje powłoki
 Powłoka zawiera przyciski znajdujące się po prawej stronie paska, za pomocą którego można powiększać lub wyłączać przepływ pracy, dopasowywać zawartość przepływu pracy do rozmiaru ekranu, a także wyświetlać lub ukrywać mapę przeglądu. Możesz również powiększyć lub pomniejszyć przepływ pracy za pomocą skrótów klawiaturowych CTRL + + i CTRL +-.

## <a name="overview-map"></a>Mapa omówienia
 Mapa przeglądu przedstawia małą wersję całego działania w bieżącym katalogu głównym, w tym wszystkie jego elementy podrzędne i wszystkie rozwinięte elementy podrzędne. Istnieje okienko ekranu, prostokąt z pomarańczowym obramowaniem, który wyróżnia część działania aktualnie wyświetlaną wewnątrz edytora. Przeciąganie prostokąta wokół mapy przeglądu powoduje przewinięcie projektanta przepływu pracy i zmianę widoku edytora.

> [!NOTE]
> Interfejs użytkownika Projektant przepływu pracy jest zwirtualizowany. Projektanci działań są renderowane tylko wtedy, gdy jest to wymagane. Jeśli część przepływu pracy nigdy nie została narysowana na powierzchni projektanta, ta część jest wyświetlana jako biała na mapie przeglądowej. Przewijanie do mapy przeglądowej całkowicie rysuje przepływ pracy.

## <a name="copying-or-saving-workflows-as-images"></a>Kopiowanie lub zapisywanie przepływów pracy jako obrazów
 Przepływy pracy można kopiować w formacie mapy bitowej lub zapisywać w formacie mapy bitowej lub wektora. Kopiowanie lub zapisywanie obrazu umożliwia wyeksportowanie widoku całego działania w bieżącym katalogu nadrzędnym, w tym wszystkich elementów podrzędnych i wszystkich ich rozwiniętych elementów podrzędnych do innego programu.

 Aby skopiować jako obraz, kliknij prawym przyciskiem myszy w dowolnym miejscu projektanta i wybierz polecenie **Kopiuj jako obraz**. Aby zapisać jako obraz, kliknij prawym przyciskiem myszy w dowolnym miejscu projektanta i wybierz polecenie **Zapisz jako obraz**. Przepływy pracy można zapisywać w formacie JPG, PNG, GIF lub XPS. Format jest wybierany w oknie dialogowym **Zapisz jako** w polu **Zapisz jako typ:** lista rozwijana w dół w dolnej części okna.

## <a name="fonts-and-colors"></a>Czcionki i kolory

Czcionki używane w Projektant przepływu pracy wewnątrz programu Visual Studio są kontrolowane przez czcionkę środowiska. Kolory wyświetlane w Projektant przepływu pracy zmienić, jeśli używasz schematu kolorów o dużym kontraście dla motywu systemu operacyjnego. Musisz ponownie uruchomić program Visual Studio po wprowadzeniu zmiany w ustawieniach czcionki lub koloru, zanim zmiany zaczną obowiązywać w Projektant przepływu pracy.