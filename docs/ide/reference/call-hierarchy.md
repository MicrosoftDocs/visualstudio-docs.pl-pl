---
title: Znajdź wywołania do metody
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77142ff9f2923ba21507327ad3f6f487b4f895ae
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960896"
---
# <a name="view-call-hierarchy"></a>Pokaż hierarchię wywołań

Wyświetlając hierarchię wywołań dla kodu, możesz przejść wszystkie wywołania do i czasami z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć przepływ kodu i oceny wpływu zmian kodu. Można sprawdzić kilka poziomów kodem, aby wyświetlić złożonych łańcuchy wywołania metody oraz dodatkowe punkty wejścia do kodu. Dzięki temu można eksplorować wszystkie możliwe wykonania ścieżki.

W programie Visual Studio możesz wyświetlić hierarchię wywołań w czasie projektowania. Oznacza to, że nie masz ustawić punkt przerwania i uruchomić debugera, aby wyświetlić stos wywołań w czasie wykonywania.

## <a name="use-the-call-hierarchy-window"></a>Korzystanie z okna hierarchię wywołań

Aby wyświetlić **hierarchię wywołań,** , kliknij prawym przyciskiem myszy w edytorze kodu na nazwę metody, właściwości lub wywołanie konstruktora, a następnie wybierz pozycję **Pokaż hierarchię wywołań,**.

Nazwa elementu członkowskiego, który pojawia się w okienku widoku drzewa, w **hierarchię wywołań** okna. Po rozwinięciu węzła elementu członkowskiego, **wywołania do** *nazwa elementu członkowskiego*, a w języku C++, **wywołania z** *nazwa elementu członkowskiego*, węzły podrzędne są wyświetlane.

Dla kodu C++ można wyświetlić wywołania do i od elementu członkowskiego:

![Hierarchia wywołań dla kodu C++ w programie Visual Studio](media/call-hierarchy-cpp.png)

Aby uzyskać C# i kodu języka Visual Basic można zobaczyć wywołania do elementu członkowskiego, ale nie wywołań:

![Wywołaj hierarchię dla C# kodu w programie Visual Studio](media/call-hierarchy-csharp.png)

- Po rozwinięciu **wywołania do** węzeł, wszystkie elementy członkowskie, że wyświetlane są wywołania wybranego elementu członkowskiego.

- Dla języka C++, f, możesz rozwinąć **wywołania z** są wyświetlane w węźle wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.

Następnie rozwiń węzeł każdego wywołania elementu członkowskiego, aby wyświetlić jego **wywołania do**i dla języka C++, **wywołania z** węzłów. Dzięki temu można nawigować do stosu wywołań, jak pokazano na poniższej ilustracji:

![Okno hierarchii wywołań o różnych poziomach rozwinięte](media/call-hierarchy-csharp-expanded.png)

Dla elementów członkowskich, które są zdefiniowane jako wirtualny lub abstrakcyjnej **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny. Te węzły można rozwijać pojawiają się na tym samym poziomie co **wywołania do** i **wywołania z** węzłów.

**Zakres wyszukiwania** na pasku narzędzi zawiera opcje dla **Moje rozwiązanie**, **bieżący projekt**, i **bieżący dokument**.

Po wybraniu podrzędny element członkowski w **hierarchię wywołań** okienku widoku drzewa:

- **Hierarchię wywołań** okienku szczegółów zostaną wyświetlone wszystkie wiersze kodu, w którym ten podrzędny element członkowski jest wywoływana z nadrzędnego elementu członkowskiego.

- **Definicji kodu** okna, jeśli jest otwarty, wyświetlany jest kod dla wybranego elementu członkowskiego (tylko C++). Aby uzyskać więcej informacji na temat tego okna, zobacz [wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> **Hierarchię wywołań** funkcji nie znajdzie metoda odwołania do grupy, która obejmuje miejsca, w którym metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć **Znajdź wszystkie odwołania** polecenia.

## <a name="shortcut-menu-items"></a>Elementy menu skrótów

W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzeł w okienku widoku drzewa.

|W Menu kontekstowym|Opis|
| - |-----------------|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł w okienku widoku drzewa jako nowy węzeł główny. Dzięki temu można skoncentrować się uwagi na określonych poddrzewo.|
|**Usuń element główny**|Usuwa wybrany główny węzeł, w okienku widoku drzewa. Ta opcja jest dostępna tylko z węzła głównego.<br /><br /> Można również użyć **Usuń głównego** przycisku paska narzędzi, aby usunąć węzeł główny wybrane.|
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji dla wybranego węzła. Powoduje to przejście do oryginalnej definicji dla wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby wykonać polecenie Przejdź do definicji, możesz kliknąć dwukrotnie wybrany węzeł lub nacisnąć klawisz F12, dla wybranego węzła.|
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania dla wybranego węzła. To umożliwia znalezienie wszystkich wierszy kodu w projekcie tego odwołanie do klasy lub elementu członkowskiego.<br /><br /> SHIFT + F12 umożliwia również Uruchom polecenie Znajdź wszystkie odwołania dla wybranego węzła.|
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzły podrzędne).|
|**Odśwież**|Zwija wybrany węzeł, aby ponownie powiększający się Wyświetla bieżące informacje.|