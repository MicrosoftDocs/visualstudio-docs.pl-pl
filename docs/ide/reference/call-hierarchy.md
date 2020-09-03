---
title: Znajdź wywołania metody
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595803"
---
# <a name="view-call-hierarchy"></a>Wyświetl hierarchię wywołań

Wyświetlając hierarchię wywołań dla kodu, można nawigować wszystkie wywołania do, a czasami z, z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć, jak przepływy kodu i oszacować skutki zmian w kodzie. Można sprawdzić kilka poziomów kodu, aby wyświetlić złożone łańcuchy wywołań metod i dodatkowe punkty wejścia do kodu. Dzięki temu można eksplorować wszystkie możliwe ścieżki wykonywania.

W programie Visual Studio można wyświetlić hierarchię wywołań w czasie projektowania. Oznacza to, że nie trzeba ustawiać punktu przerwania i uruchomić debugera, aby wyświetlić stos wywołań czasu wykonywania.

## <a name="use-the-call-hierarchy-window"></a>Korzystanie z okna hierarchia wywołań

Aby wyświetlić okno **Hierarchia wywołań** , kliknij prawym przyciskiem myszy w edytorze kodu na nazwie metody, właściwości lub konstruktora wywołania, a następnie wybierz pozycję **Wyświetl hierarchię wywołań**.

Nazwa elementu członkowskiego jest wyświetlana w okienku widoku drzewa w oknie **Hierarchia wywołań** . Jeśli rozszerzasz węzeł elementu członkowskiego, **wywołania do** *nazwy elementu członkowskiego*i dla języka C++, będą wyświetlane **wywołania z** *nazwy elementu członkowskiego*.

W przypadku kodu C++ można zobaczyć wywołania zarówno do, jak i z elementu członkowskiego:

![Hierarchia wywołań dla kodu C++ w programie Visual Studio](media/call-hierarchy-cpp.png)

W przypadku kodu C# i Visual Basic, można zobaczyć wywołania do elementu członkowskiego, ale nie wywołania z:

![Hierarchia wywołań dla kodu C# w programie Visual Studio](media/call-hierarchy-csharp.png)

- Po rozszerzeniu **wywołań do** węzła zostaną wyświetlone wszystkie elementy członkowskie, które wywołują wybrany element członkowski.

- W przypadku języka C++, f rozszerzane są **wywołania z** węzła, zostaną wyświetlone wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.

Następnie można rozwinąć każdy wywołujący element członkowski, aby zobaczyć jego **wywołania do**, i dla języka C++, **wywołania z** węzłów. Pozwala to na przejście do stosu obiektów wywołujących, jak pokazano na poniższej ilustracji:

![Okno hierarchii wywołań z rozwiniętymi wieloma poziomami](media/call-hierarchy-csharp-expanded.png)

W przypadku elementów członkowskich, które są zdefiniowane jako wirtualne lub abstrakcyjne, zostanie wyświetlony węzeł **Nazwa metody zastąpień** . W przypadku elementów członkowskich interfejsu pojawia się węzeł **Nazwa metody implementującej** . Te węzły rozszerzalne pojawiają się na tym samym poziomie co **wywołania** i **wywołania z** węzłów.

Pole **zakres wyszukiwania** na pasku narzędzi zawiera opcje dla **mojego rozwiązania**, **bieżącego projektu**i **bieżącego dokumentu**.

Po wybraniu podrzędnego elementu członkowskiego w okienku widoku drzewa **hierarchii wywołań** :

- W okienku Szczegóły **hierarchii wywołań** są wyświetlane wszystkie wiersze kodu, w których ten podrzędny element członkowski jest wywoływany z nadrzędnego elementu członkowskiego.

- Okno **definicji kodu** , jeśli otwarte, wyświetla kod dla wybranego elementu członkowskiego (tylko C++). Aby uzyskać więcej informacji na temat tego okna, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Funkcja **hierarchii wywołań** nie znajduje odwołań do grup metod, w tym miejsc, w których metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisana do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć polecenia **Znajdź wszystkie odwołania** .

## <a name="shortcut-menu-items"></a>Elementy menu skrótów

W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzła w okienku widoku drzewa.

|Element menu kontekstowego|Opis|
| - |-----------------|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł do okienka widoku drzewa jako nowy węzeł główny. Dzięki temu można skoncentrować uwagę na określonym poddrzewie.|
|**Usuń element główny**|Usuwa wybrany węzeł główny z okienka widoku drzewa. Ta opcja jest dostępna tylko z poziomu węzła głównego.<br /><br /> Możesz również użyć przycisku **Usuń główny** pasek narzędzi, aby usunąć wybrany węzeł główny.|
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji w wybranym węźle. Spowoduje to przejście do oryginalnej definicji wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby uruchomić polecenie Przejdź do definicji, można również kliknąć dwukrotnie wybrany węzeł lub nacisnąć klawisz F12 w wybranym węźle.|
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania w wybranym węźle. Spowoduje to znalezienie wszystkich wierszy kodu w projekcie, które odwołują się do klasy lub składowej.<br /><br /> Możesz również użyć klawiszy SHIFT + F12, aby uruchomić polecenie Znajdź wszystkie odwołania w wybranym węźle.|
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzłów podrzędnych).|
|**Odświeżanie**|Zwija zaznaczony węzeł, tak aby jego ponowne rozwinięcie zawierało bieżące informacje.|
