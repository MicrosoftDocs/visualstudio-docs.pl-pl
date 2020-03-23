---
title: 'Porady: tworzenie typów za pomocą Projektanta klas'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881a8ed7f1aceb5f97eaed1f0b9285951d1d39f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590179"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Jak: Tworzenie typów przy użyciu Projektanta klas

Aby zaprojektować nowe typy dla projektów języka C# i Visual Basic, należy utworzyć je na diagramie klas. Aby wyświetlić istniejące typy, zobacz [Jak: Wyświetlanie istniejących typów](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a>Tworzenie nowego typu

1. W **przyborniku**w obszarze **Projektant klas**przeciągnij jeden z nich na diagram klas:

    - **Klasa** lub **klasa abstrakcyjna**

    - **Wyliczenie**

    - **Interface**

    - **Struktura** (VB) lub **Struktura** (C#)

    - **Delegata**

    - **Moduł** (tylko VB)

2. Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.

3. Wybierz plik, do którego chcesz dodać kod początkowy dla typu:

    - Aby utworzyć nowy plik i dodać go do bieżącego projektu, wybierz pozycję **Utwórz nowy plik** i nazwij plik.

    - Aby dodać kod do istniejącego pliku, wybierz pozycję **Dodaj do istniejącego pliku**.

         Jeśli rozwiązanie ma projekt, który udostępnia kod w wielu aplikacjach, można dodać nowy typ do diagramu klasy w projekcie aplikacji, ale tylko wtedy, gdy odpowiedni plik klasy znajduje się w tym samym projekcie aplikacji lub znajduje się w projekcie udostępnionym.

4. Teraz dodaj inne elementy, aby zdefiniować typ:

    |||
    |-|-|
    |**For**|**Dodaj**|
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|
    |Delegate|Parametry, które definiują obiekt delegowany|
    |Moduł|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|

     Zobacz [Tworzenie członków](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a>Stosowanie atrybutu niestandardowego do typu

1. Kliknij typ kształtu na diagramie klasy.

2. W **pozycji Właściwości**, obok właściwości **Atrybuty niestandardowe** dla typu, kliknij przycisk wielokropek (...) .

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a>Stosowanie atrybutu niestandardowego do elementu członkowskiego typu

1. Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.

2. W **właściwości ,** znajdź element **członkowski atrybuty niestandardowe** właściwości.

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Jak: Tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Tworzenie i konfigurowanie składowych typu](creating-and-configuring-type-members.md)
- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
