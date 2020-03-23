---
title: Znajdowanie wywołań metody
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcedc6a49c0df84b4482f8030524d59d4336bcc8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595803"
---
# <a name="view-call-hierarchy"></a>Wyświetlanie hierarchii połączeń

Przeglądając hierarchię wywołań dla kodu, można nawigować wszystkie wywołania do, a czasami z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć, jak przepływy kodu i do oceny skutków zmian w kodzie. Można zbadać kilka poziomów kodu, aby wyświetlić złożone łańcuchy wywołań metody i dodatkowe punkty wejścia do kodu. Dzięki temu można eksplorować wszystkie możliwe ścieżki wykonywania.

W programie Visual Studio można wyświetlić hierarchię wywołań w czasie projektowania. Oznacza to, że nie trzeba ustawić punkt przerwania i uruchomić debugera, aby wyświetlić stos wywołań w czasie wykonywania.

## <a name="use-the-call-hierarchy-window"></a>Okno Hierarchia połączeń

Aby wyświetlić okno **Hierarchia połączeń,** kliknij prawym przyciskiem myszy w edytorze kodu nazwę metody, właściwości lub wywołania konstruktora, a następnie wybierz polecenie **Wyświetl hierarchię wywołań**.

Nazwa elementu członkowskiego pojawia się w okienku widoku drzewa w oknie **Hierarchia połączeń.** Jeśli rozwiniesz węzeł elementu członkowskiego, **wywołana** *nazwa elementu członkowskiego*, a dla języka C++, **wywołana** *nazwa elementu członkowskiego*, pojawią się poddęty.

W przypadku kodu języka C++ można zobaczyć wywołania zarówno do, jak i z elementu członkowskiego:

![Hierarchia połączeń dla kodu języka C++ w programie Visual Studio](media/call-hierarchy-cpp.png)

W przypadku kodu języka C# i Visual Basic można zobaczyć wywołania do członka, ale nie wywołania z:

![Hierarchia połączeń dla kodu języka C# w programie Visual Studio](media/call-hierarchy-csharp.png)

- Jeśli rozwiniesz węzeł **Wywołania do,** zostaną wyświetlone wszystkie elementy członkowskie, które wywołują wybrany element członkowski.

- W przypadku języka C++f można rozwinąć węzeł **Wywołania z,** wyświetlane są wszystkie elementy członkowskie wywoływane przez wybranego członka.

Następnie można rozwinąć każdego członka wywołującego, aby wyświetlić jego **wywołania do**, a dla C++, **wywołania z** węzłów. Dzięki temu można przejść do stosu rozmówców, jak pokazano na poniższej ilustracji:

![Okno Hierarchia połączeń z rozszerzonym wieloma poziomami](media/call-hierarchy-csharp-expanded.png)

Dla elementów członkowskich, które są zdefiniowane jako wirtualne lub abstrakcyjne, zastępuje węzeł **nazwy metody.** Dla elementów członkowskich interfejsu pojawia się węzeł **nazwa metody implementuje.** Te rozszerzalne węzły są wyświetlane na tym samym poziomie co **węzły wywołania** i **wywołania z.**

Pole **Zakres wyszukiwania** na pasku narzędzi zawiera opcje dla opcji Moje **rozwiązanie,** **Bieżący projekt**i **Bieżący dokument**.

Po wybraniu elementu podrzędnego w okienku widoku drzewa **hierarchii połączeń:**

- W okienku szczegółów **hierarchii połączeń** są wyświetlane wszystkie wiersze kodu, w których ten element podrzędny jest wywoływany z nadrzędnego elementu członkowskiego.

- Okno **Definicja kodu,** jeśli jest otwarte, wyświetla kod dla wybranego elementu członkowskiego (tylko C++). Aby uzyskać więcej informacji na temat tego okna, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Funkcja **hierarchii wywołań** nie znajduje odwołań do grup metod, która obejmuje miejsca, w których metoda jest dodawana jako program obsługi zdarzeń lub jest przypisana do pełnomocnika. Aby znaleźć wszystkie odwołania do metody, można użyć polecenia **Znajdź wszystkie odwołania.**

## <a name="shortcut-menu-items"></a>Elementy menu skrótów

W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzła w okienku widoku drzewa.

|Element menu kontekstowego|Opis|
| - |-----------------|
|**Dodaj jako nowy katalog główny**|Dodaje zaznaczony węzeł do okienka widoku drzewa jako nowy węzeł główny. Dzięki temu można skupić uwagę na określonym poddrzewie.|
|**Usuń katalog główny**|Usuwa zaznaczony węzeł główny z okienka widoku drzewa. Ta opcja jest dostępna tylko z węzła głównego.<br /><br /> Można również użyć przycisku Usuń pasek narzędzi **Root,** aby usunąć wybrany węzeł główny.|
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji w wybranym węźle. Spowoduje to przejście do oryginalnej definicji wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby uruchomić polecenie Przejdź do definicji, można również dwukrotnie kliknąć zaznaczony węzeł lub nacisnąć klawisz F12 w wybranym węźle.|
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania w wybranym węźle. Spowoduje to znalezienie wszystkich wierszy kodu w projekcie, które odwołują się do klasy lub elementu członkowskiego.<br /><br /> Można również użyć klawiszy SHIFT+F12, aby uruchomić polecenie Znajdź wszystkie odwołania w wybranym węźle.|
|**Kopii**|Kopiuje zawartość wybranego węzła (ale nie jego węzłów podrzędnych).|
|**Odświeżanie**|Zwija wybrany węzeł, tak aby ponowne rozwinięcie go wyświetla bieżące informacje.|
