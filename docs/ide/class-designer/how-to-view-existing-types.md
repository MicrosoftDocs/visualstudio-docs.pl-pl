---
title: 'Porady: wyświetlanie istniejących typów (Projektant klas)'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: fa27489844bc59bc0d4da32440cc1caa74ecbea6
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770011"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Instrukcje: wyświetlanie istniejących typów w Projektant klas

Aby wyświetlić istniejący typ i jego elementy członkowskie, Dodaj kształt do diagramu klas.

Można zobaczyć typy lokalne i typy odwołania. Typ lokalny istnieje w aktualnie otwartym projekcie i jest do odczytu/zapisu. Typ odwołania istnieje w innym projekcie lub w zestawie odwołania i jest tylko do odczytu.

Aby zaprojektować nowe typy na diagramach klas, zobacz [jak: Tworzenie typów za pomocą Projektant klas](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Aby wyświetlić typy w projekcie na diagramie klasy

1. Z projektu w **Eksplorator rozwiązań**Otwórz istniejący plik diagramu klasy (. CD). Lub jeśli nie istnieje żaden diagram klas, dodaj nowy diagram klas do projektu. Zobacz [jak: dodać diagramy klas do projektów](how-to-add-class-diagrams-to-projects.md).

2. Z projektu w **Eksplorator rozwiązań**przeciągnij plik kodu źródłowego do diagramu klas.

    > [!NOTE]
    > Jeśli rozwiązanie ma projekt, który współużytkuje kod w wielu aplikacjach, możesz przeciągnąć pliki lub kod do diagramu klasy tylko z tych źródeł:
    >
    > - Projekt aplikacji, który zawiera diagram
    > - Projekt współużytkowany, który został zaimportowany przez projekt aplikacji
    > - Projekt odwołania
    > - Zestaw

    Kształty przedstawiające typy zdefiniowane w pliku kodu źródłowego są wyświetlane na diagramie w miejscu, gdzie przeciągnąłeś plik.

Możesz również wyświetlić typy w projekcie, przeciągając jeden lub więcej typów z węzła projektu w **Widok klasy** do diagramu klas.

> [!TIP]
> Jeśli **Widok klasy** nie jest otwarty, Otwórz **Widok klasy** z menu **Widok** .

Aby wyświetlić typy w lokalizacjach domyślnych na diagramie, wybierz jeden lub więcej typów w **Widok klasy**, kliknij prawym przyciskiem myszy wybrane typy i wybierz polecenie **Wyświetl Diagram klas**.

> [!NOTE]
> Jeśli zamknięty diagram klas zawierający typ już istnieje w projekcie, diagram klas się otworzy, aby wyświetlić kształt typu. Jeśli jednak żaden Diagram klas zawierający typ nie istnieje w projekcie, **Projektant klas** utworzy nowy Diagram klas w projekcie i otworzy go, aby wyświetlić typ.

Przy pierwszym wyświetleniu typu na diagramie, jego kształt pojawia się domyślnie zwinięty. Można rozwinąć kształt, aby wyświetlić jego zawartość.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Aby wyświetlić zawartość projektu w diagramie klas

W **Eksplorator rozwiązań** lub **Widok klasy**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Widok**, a następnie wybierz polecenie **Wyświetl Diagram klas**. Tworzony jest automatycznie wypełniony Diagram klas.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Instrukcje: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
