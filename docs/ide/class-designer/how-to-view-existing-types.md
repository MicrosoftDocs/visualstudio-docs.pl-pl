---
title: 'Porady: wyświetlanie istniejących typów (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588710"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Jak: Wyświetlanie istniejących typów w Projektancie klas

Aby wyświetlić istniejący typ i jego elementy członkowskie, dodaj jego kształt do diagramu klasy.

Można zobaczyć typy lokalne i typy odwołania. Typ lokalny istnieje w aktualnie otwartym projekcie i jest do odczytu/zapisu. Typ odwołania istnieje w innym projekcie lub w zestawie odwołania i jest tylko do odczytu.

Aby zaprojektować nowe typy na diagramach klas, zobacz [Jak: Tworzenie typów przy użyciu projektanta klas](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Aby wyświetlić typy w projekcie na diagramie klasy

1. Z projektu w **Eksploratorze rozwiązań**otwórz istniejący plik diagramu klasy (cd). Lub jeśli nie istnieje żaden diagram klas, dodaj nowy diagram klas do projektu. Zobacz [Jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md).

2. Z projektu w **Eksploratorze rozwiązań**przeciągnij plik kodu źródłowego na diagram klasy.

    > [!NOTE]
    > Jeśli rozwiązanie ma projekt, który udostępnia kod w wielu aplikacjach, można przeciągnąć pliki lub kod do diagramu klasy tylko z tych źródeł:
    >
    > - Projekt aplikacji zawierający diagram
    > - Udostępniony projekt zaimportowany przez projekt aplikacji
    > - Projekt odwołania
    > - Zestaw

    Kształty przedstawiające typy zdefiniowane w pliku kodu źródłowego są wyświetlane na diagramie w miejscu, gdzie przeciągnąłeś plik.

Można również wyświetlić typy w projekcie, przeciągając jeden lub więcej typów z węzła projektu w **widoku klasy** do diagramu klasy.

> [!TIP]
> Jeśli **widok klasy** nie jest otwarty, otwórz widok **klasy** z menu **Widok.**

Aby wyświetlić typy w lokalizacjach domyślnych na diagramie, wybierz jeden lub więcej typów w **widoku klasy,** kliknij prawym przyciskiem myszy wybrane typy i wybierz polecenie **Wyświetl diagram klas**.

> [!NOTE]
> Jeśli zamknięty diagram klas zawierający typ już istnieje w projekcie, diagram klas się otworzy, aby wyświetlić kształt typu. Jeśli jednak w projekcie nie istnieje żaden diagram klasy zawierający typ, **projektant klas** tworzy nowy diagram klas w projekcie i otwiera go, aby wyświetlić typ.

Przy pierwszym wyświetleniu typu na diagramie, jego kształt pojawia się domyślnie zwinięty. Można rozwinąć kształt, aby wyświetlić jego zawartość.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Aby wyświetlić zawartość projektu na diagramie klas

W **Eksploratorze rozwiązań** lub **widoku klasy**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Widok**, a następnie wybierz polecenie Wyświetl **diagram klas**. Tworzony jest automatycznie wypełniony Diagram klas.

## <a name="see-also"></a>Zobacz też

- [Jak: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Jak: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
