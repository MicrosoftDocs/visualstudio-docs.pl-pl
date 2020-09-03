---
title: Hierarchia wywołań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 823c61e7625850c680b52cd4ad9386ef0838d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660931"
---
# <a name="call-hierarchy"></a>Hierarchia wywołań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hierarchia wywołań umożliwia nawigowanie po kodzie przez wyświetlanie wszystkich wywołań do i z wybranej metody, właściwości lub konstruktora. Dzięki temu można lepiej zrozumieć, jak przepływy kodu i oszacować skutki zmian w kodzie. Można sprawdzić kilka poziomów kodu, aby wyświetlić złożone łańcuchy wywołań metod i dodatkowe punkty wejścia do kodu, co umożliwia Eksplorowanie wszystkich możliwych ścieżek wykonywania.

 Hierarchia wywołań jest dostępna w czasie projektowania, w przeciwieństwie do stosu wywołań, który jest wyświetlany przez debuger.

## <a name="using-call-hierarchy"></a>Korzystanie z hierarchii wywołań
 Aby wyświetlić okno **Hierarchia wywołań** , kliknij prawym przyciskiem myszy nazwę metody, właściwości lub konstruktora wywołania, a następnie kliknij pozycję **Wyświetl hierarchię wywołań**.

 Nazwa elementu członkowskiego jest wyświetlana w okienku widoku drzewa w oknie **Hierarchia wywołań** . Jeśli rozszerzasz węzeł elementu członkowskiego, zostaną wyświetlone **wywołania**_nazwy elementu członkowskiego_ i **wywołania z**podwęzłów_Nazwa elementu członkowskiego_ . Na poniższej ilustracji przedstawiono te węzły w oknie **Hierarchia wywołań** .

 ![Hierarchia wywołań z otwartym jednym węzłem](../../ide/reference/media/onenode.png "OneNode") Okno hierarchii wywołań

- Po rozszerzeniu **wywołań do** węzła zostaną wyświetlone wszystkie elementy członkowskie, które wywołują wybrany element członkowski.

- W przypadku rozszerzenia **wywołań z** węzła zostaną wyświetlone wszystkie elementy członkowskie, które są wywoływane przez wybrany element członkowski.

  Następnie można rozwinąć każdy z tych elementów podrzędnych węzła do **wywołań** i **wywołań z** węzłów. Pozwala to na przejście do stosu obiektów wywołujących, jak pokazano na poniższej ilustracji.

  ![Otwórz hierarchię wywołań z wieloma węzłami](../../ide/media/multiplenodes.png "MultipleNodes") Okno hierarchii wywołań

  W przypadku elementów członkowskich, które są zdefiniowane jako wirtualne lub abstrakcyjne, zostanie wyświetlony węzeł **Nazwa metody zastąpień** . W przypadku elementów członkowskich interfejsu pojawia się węzeł **Nazwa metody implementującej** . Te węzły rozszerzalne pojawiają się na tym samym poziomie co **wywołania** i **wywołania z** węzłów.

  Pole **zakres wyszukiwania** na pasku narzędzi zawiera opcje dla **mojego rozwiązania**, **bieżącego projektu**i **bieżącego dokumentu**.

  Po wybraniu podrzędnego elementu członkowskiego w okienku widoku drzewa **hierarchii wywołań** :

- W okienku Szczegóły **hierarchii wywołań** są wyświetlane wszystkie wiersze kodu, w których ten podrzędny element członkowski jest wywoływany z nadrzędnego elementu członkowskiego.

- **Okno definicji kodu**, jeśli jest otwarte, wyświetla kod dla wybranego elementu członkowskiego. To okno jest dostępne w językach C# i C++. Aby uzyskać więcej informacji na temat tego okna, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> W hierarchii wywołań nie znajdują się odwołania do grup metod, w tym miejsca, w których metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisana do delegata. Aby znaleźć wszystkie odwołania do metody, można użyć polecenia **Znajdź wszystkie odwołania** .

## <a name="shortcut-menu-items"></a>Elementy menu skrótów
 W poniższej tabeli opisano kilka opcji menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy węzła w okienku widoku drzewa.

|Element menu kontekstowego|Opis|
|-----------------------|-----------------|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł do okienka widoku drzewa jako nowy węzeł główny. Dzięki temu można skoncentrować uwagę na określonym poddrzewie.|
|**Usuń element główny**|Usuwa wybrany węzeł główny z okienka widoku drzewa. Ta opcja jest dostępna tylko z poziomu węzła głównego.<br /><br /> Możesz również użyć przycisku **Usuń główny** pasek narzędzi, aby usunąć wybrany węzeł główny.|
|**Przejdź do definicji**|Uruchamia polecenie Przejdź do definicji w wybranym węźle. Spowoduje to przejście do oryginalnej definicji wywołania elementu członkowskiego lub definicji zmiennej.<br /><br /> Aby uruchomić polecenie Przejdź do definicji, można również kliknąć dwukrotnie wybrany węzeł lub nacisnąć klawisz F12 w wybranym węźle.|
|**Znajdź wszystkie odwołania**|Uruchamia polecenie Znajdź wszystkie odwołania w wybranym węźle. Spowoduje to znalezienie wszystkich wierszy kodu w projekcie, które odwołują się do klasy lub składowej.<br /><br /> Możesz również użyć klawiszy SHIFT + F12, aby uruchomić polecenie Znajdź wszystkie odwołania w wybranym węźle.|
|**Kopiuj**|Kopiuje zawartość wybranego węzła (ale nie jego węzłów podrzędnych).|
|**Odświeżanie**|Zwija zaznaczony węzeł, tak aby jego ponowne rozwinięcie zawierało bieżące informacje.|
