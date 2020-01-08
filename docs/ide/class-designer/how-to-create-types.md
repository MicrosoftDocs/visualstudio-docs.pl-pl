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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590179"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Instrukcje: Tworzenie typów za pomocą Projektant klas

Aby zaprojektować nowe C# typy dla projektów i Visual Basic, utwórz je na diagramie klas. Aby wyświetlić istniejące typy, zobacz [How to: View Existing Types](how-to-view-existing-types.md).

## <a name="CreateType"></a>Utwórz nowy typ

1. W **przyborniku**w obszarze **Projektant klas**przeciągnij jeden z nich na Diagram klas:

    - **Klasa** lub **Klasa abstrakcyjna**

    - **Enum**

    - **Interface**

    - **Structure** (VB) lub **struct** (C#)

    - **Delegate**

    - **Moduł** (tylko w języku VB)

2. Nadaj nazwę typowi. Następnie wybierz jego poziom dostępu.

3. Wybierz plik, do którego chcesz dodać kod początkowy dla typu:

    - Aby utworzyć nowy plik i dodać go do bieżącego projektu, wybierz opcję **Utwórz nowy plik** i Nazwij plik.

    - Aby dodać kod do istniejącego pliku, wybierz pozycję **Dodaj do istniejącego pliku**.

         Jeśli rozwiązanie ma projekt, który współużytkuje kod w wielu aplikacjach, można dodać nowy typ do diagramu klasy w projekcie aplikacji, ale tylko wtedy, gdy odpowiedni plik klasy znajduje się w tym samym projekcie aplikacji lub znajduje się w projekcie udostępnionym.

4. Teraz dodaj inne elementy, aby zdefiniować typ:

    |||
    |-|-|
    |**Dla**|**Dodaj**|
    |Klasy, klasy abstrakcyjne, struktury i obiekty struct|Metody, właściwości, pola, zdarzenia, konstruktory (metoda), destruktory (metoda) i stałe, które określają typ|
    |Wyliczenia|Wartości pól, które tworzą wyliczenie|
    |Interfejsy|Metody, właściwości i zdarzenia, które tworzą interfejs|
    |Delegate|Parametry, które definiują obiekt delegowany|
    |Module|Metody, właściwości, pola, zdarzenia, konstruktory (metoda) i stałe, które określają moduł|

     Zobacz [Tworzenie elementów członkowskich](creating-and-configuring-type-members.md#create-members).

## <a name="CustAttributeType"></a>Zastosuj atrybut niestandardowy do typu

1. Kliknij typ kształtu na diagramie klasy.

2. We **właściwościach**obok właściwości **atrybuty niestandardowe** typu kliknij przycisk wielokropka (...).

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="CustAttributeMember"></a>Zastosuj atrybut niestandardowy do elementu członkowskiego typu

1. Kliknij nazwę składowej w jej kształcie typu na diagramie klasy lub kliknij jej wiersz w oknie Szczegóły klasy.

2. We **właściwościach**Znajdź właściwość **atrybuty niestandardowe** elementu członkowskiego.

3. Dodaj jeden lub więcej atrybutów niestandardowych, jeden na wiersz. Nie otaczaj ich nawiasami kwadratowymi.

   Atrybuty niestandardowe są stosowane do typu.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Instrukcje: tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Tworzenie i konfigurowanie składowych typu](creating-and-configuring-type-members.md)
- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
