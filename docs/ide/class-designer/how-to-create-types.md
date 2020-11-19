---
title: 'Porady: tworzenie typów za pomocą Projektanta klas'
description: Dowiedz się, jak projektować nowe typy dla projektów C# i Visual Basic, tworząc je na diagramie klas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ac6e59f4dc6fa68962ac061132e3fab90ec8e955
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901443"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Instrukcje: Tworzenie typów za pomocą Projektant klas

Aby zaprojektować nowe typy dla projektów C# i Visual Basic, utwórz je na diagramie klas. Aby wyświetlić istniejące typy, zobacz [How to: View Existing Types](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Utwórz nowy typ

1. W **przyborniku** w obszarze **Projektant klas** przeciągnij jeden z nich na Diagram klas:

    - **Klasa** lub **Klasa abstrakcyjna**

    - **Wyliczenie**

    - **Interfejs**

    - **Structure** (VB) lub **Struktura** (C#)

    - **Delegat**

    - **Moduł** (tylko w języku VB)

2. Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.

3. Wybierz plik, do którego chcesz dodać kod początkowy dla typu:

    - Aby utworzyć nowy plik i dodać go do bieżącego projektu, wybierz opcję **Utwórz nowy plik** i Nazwij plik.

    - Aby dodać kod do istniejącego pliku, wybierz pozycję **Dodaj do istniejącego pliku**.

         Jeśli rozwiązanie ma projekt, który współużytkuje kod w wielu aplikacjach, można dodać nowy typ do diagramu klasy w projekcie aplikacji, ale tylko wtedy, gdy odpowiedni plik klasy znajduje się w tym samym projekcie aplikacji lub znajduje się w projekcie udostępnionym.

4. Teraz dodaj inne elementy, aby zdefiniować typ:

    |**Dla**|**Dodaj**|
    |-|-|
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|
    |Delegat|Parametry, które definiują obiekt delegowany|
    |Moduł|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|

     Zobacz [Tworzenie elementów członkowskich](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Zastosuj atrybut niestandardowy do typu

1. Kliknij typ kształtu na diagramie klasy.

2. We **właściwościach** obok właściwości **atrybuty niestandardowe** typu kliknij przycisk wielokropka (...).

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Zastosuj atrybut niestandardowy do elementu członkowskiego typu

1. Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.

2. We **właściwościach** Znajdź właściwość **atrybuty niestandardowe** elementu członkowskiego.

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Instrukcje: tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Tworzenie i konfigurowanie składowych typu](creating-and-configuring-type-members.md)
- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
