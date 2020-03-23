---
title: Użyj Projektanta klas
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65be2b5afe91f9ee20a5eecde57d790a0cbcb2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590400"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Projektowanie i wyświetlanie klas i typów za pomocą projektanta klas

Projektowanie, wizualizacja i refaktoryzowania klas i innych typów w kodzie z **Projektantem klas** w programie Visual Studio. Diagramy klas służą do tworzenia i edytowania klas w projekcie C#, Visual Basic lub C++. Diagramy klas można również użyć, aby lepiej zrozumieć strukturę projektu lub zreorganizować kod.

## <a name="what-you-can-do-with-class-diagrams"></a>Co można zrobić z diagramami klas

- **Projekt:** Edytuj kod projektu, edytując diagram klas. Dodaj nowe elementy i usuń niechciane. Zmiany są odzwierciedlane w kodzie.

- **Wizualizuj:** Poznaj strukturę projektu, wyświetlając klasy w projekcie na diagramie. Dostosuj diagram, aby skupić się na szczegółach projektu, na których najbardziej Ci zależy. Zapisz diagram, aby użyć go później do demonstracji lub dokumentacji.

- **Refaktoryzator:** Zastępowanie metod, zmienianie nazw identyfikatorów, parametrów refaktoryzowania oraz implementowanie interfejsów i klas abstrakcyjnych.

## <a name="view-types-and-relationships"></a>Wyświetlanie typów i relacji

Diagramy klas pokazują szczegóły typów, na przykład ich składników członkowskich i relacji między nimi. Wizualizacja tych jednostek jest dynamicznym widokiem do kodu. Oznacza to, że można edytować typy w projektancie, a następnie wyświetlić zmiany odzwierciedlone w kodzie źródłowym encji. Podobnie diagram klas jest synchronizowany ze zmianami wprowadzanych w plikach kodu.

> [!NOTE]
> Jeśli projekt zawiera diagram klasy i projekt odwołuje się do typu, który znajduje się w innym projekcie, diagram klasy nie pokazuje typu, do którego istnieje odwołanie, dopóki nie skompilujesz projektu dla tego typu. Podobnie diagram nie wyświetla zmian w kodzie jednostki zewnętrznej, dopóki nie odbudujesz projektu dla tej jednostki.

## <a name="class-diagram-workflow"></a>Przepływ pracy diagramu klas

Diagramy klas mogą pomóc w zrozumieniu struktury klas projektów. Te projekty mogły zostać utworzone przez innych deweloperów lub wystarczy odświeżyć projekt, który utworzyłeś samodzielnie. Diagramy klas można używać do dostosowywania, udostępniania i prezentowania informacji o projekcie innym osobom.

Pierwszym krokiem w prezentacji informacji o projekcie jest utworzenie diagramu klas, który wyświetla, co chcesz pokazać. Aby uzyskać więcej informacji, zobacz [Dodawanie diagramu klas](how-to-add-class-diagrams-to-projects.md). Można utworzyć wiele diagramów klas dla projektu, który może służyć do wyświetlania odrębnego widoku projektu, wybranego podzbioru typów projektu lub wybranego podzbioru elementów członkowskich typów.

Oprócz definiowania, co pokazuje każdy diagram klasy, można również zmienić sposób prezentowania informacji; Aby uzyskać więcej informacji, zobacz [Jak: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md).

Po dostrojonym co najmniej jednym diagramie klas można skopiować je do dokumentów pakietu Microsoft Office i wydrukować lub wyeksportować jako pliki obrazów. Aby uzyskać więcej informacji, zobacz [Jak: Kopiowanie elementów diagramu klasy do dokumentu pakietu Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Jak: Drukowanie diagramów klas](how-to-print-class-diagrams.md) i [Jak: Eksport diagramy klas jako obrazy](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Projektant klas nie śledzi lokalizacji plików źródłowych, więc zmiana struktury projektu lub przenoszenie plików źródłowych w projekcie może spowodować, że projektant klas utracił śledzenie tego typu, zwłaszcza typ źródła typedef, klas podstawowych lub typów skojarzeń. Może pojawić się błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij zmodyfikowany lub przeniesiony kod źródłowy do diagramu klasy ponownie, aby ponownie go wyświetlić.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../writing-code-in-the-code-and-text-editor.md)
- [Zależności mapy w ramach rozwiązań](../../modeling/map-dependencies-across-your-solutions.md)
