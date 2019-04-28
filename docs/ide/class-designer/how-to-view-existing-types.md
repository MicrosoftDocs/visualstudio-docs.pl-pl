---
title: 'Instrukcje: Wyświetlanie istniejących typów (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef2882fec8d213c38a2e125d4e3f0c3f22d1d581
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975167"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Instrukcje: Wyświetlanie istniejących typów w Projektancie klas

Aby wyświetlić istniejący typ i jej elementów członkowskich, należy dodać jego kształtu do diagramu klas.

Można zobaczyć typy lokalne i typy odwołania. Typ lokalny istnieje w aktualnie otwartym projekcie i jest do odczytu/zapisu. Typ odwołania istnieje w innym projekcie lub w zestawie odwołania i jest tylko do odczytu.

Aby zaprojektować nowe typy diagramów klas, zobacz [jak: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Aby wyświetlić typy w projekcie na diagramie klasy

1. Z projektu w **Eksploratora rozwiązań**, otwórz istniejący plik diagramu klasy (.cd). Lub jeśli nie istnieje żaden diagram klas, dodaj nowy diagram klas do projektu. Zobacz [jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md).

2. Z projektu w **Eksploratora rozwiązań**, przeciągnij plik kodu źródłowego do diagramu klas.

    > [!NOTE]
    > Jeśli rozwiązanie ma projektu, który udostępnia kod przez wiele aplikacji, można przeciągnąć pliki lub kod do diagramu klasy tylko z tych źródeł:
    >
    > - Projekt aplikacji, który zawiera diagram
    > - Współdzielony projekt zaimportowany przez projekt aplikacji
    > - Projekt odwołania
    > - Zestaw

    Kształty przedstawiające typy zdefiniowane w pliku kodu źródłowego są wyświetlane na diagramie w miejscu, gdzie przeciągnąłeś plik.

Możesz również wyświetlić typy w projekcie, przeciągając jeden lub więcej typów z węzła projektu w **Widok klas** do diagramu klas.

> [!TIP]
> Jeśli **Widok klas** nie jest otwarty, otwórz **Widok klas** z **widoku** menu.

Aby wyświetlić typy w lokalizacjach domyślnych na diagramie, zaznacz jeden lub więcej typów w **Widok klas**, kliknij prawym przyciskiem myszy wybrane typy i wybierz **Pokaż Diagram klas**.

> [!NOTE]
> Jeśli zamknięty diagram klas zawierający typ już istnieje w projekcie, diagram klas się otworzy, aby wyświetlić kształt typu. Jednak jeśli nie diagram klas zawierający typ znajduje się w projekcie, **projektanta klas** tworzy nowy diagram klas w projekcie i otwiera go, aby wyświetlić typ.

Przy pierwszym wyświetleniu typu na diagramie, jego kształt pojawia się domyślnie zwinięty. Można rozwinąć kształt, aby wyświetlić jego zawartość.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Aby wyświetlić zawartość projektu na diagramie klasy

W **Eksploratora rozwiązań** lub **Widok klas**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **widoku**, następnie wybierz **Pokaż Diagram klas**. Tworzony jest automatycznie wypełniony Diagram klas.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Instrukcje: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)