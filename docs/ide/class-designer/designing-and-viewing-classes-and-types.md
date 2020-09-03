---
title: Użyj Projektant klas
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
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
ms.openlocfilehash: 80668f3b999d9e022de3d22abb383f2dbd10730a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87507914"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Projektowanie i wyświetlanie klas i typów z Projektant klas

Zaprojektowanie, wizualizowanie i Refaktoryzacja klas oraz innych typów w kodzie przy użyciu **Projektant klas** w programie Visual Studio. Diagramy klas służą do tworzenia i edytowania klas w projekcie C#, Visual Basic lub C++. Można również użyć diagramów klas, aby zrozumieć swoją strukturę projektu lepiej lub zreorganizować swój kod.

## <a name="what-you-can-do-with-class-diagrams"></a>Co można zrobić za pomocą diagramów klas

- **Projekt**: Edytuj kod projektu, edytując diagram klas. Dodaj nowe elementy i Usuń niepożądane. Zmiany zostaną odzwierciedlone w kodzie.

- **Wizualizuj**: zrozumienie struktury projektu przez przeglądanie klas w projekcie na diagramie. Dostosuj diagram tak, aby można było skupić się na szczegółach projektu, które Cię interesują. Zapisz swój diagram do użycia w dalszej części demonstracyjnej lub dokumentacji.

- **Refaktoryzacja**: zastępowanie metod, zmienianie nazw identyfikatorów, parametrów refaktoryzacji i implementowanie interfejsów i klas abstrakcyjnych.

## <a name="view-types-and-relationships"></a>Wyświetlanie typów i relacji

Diagramy klas przedstawiają szczegóły typów, na przykład ich składowe i relacje między nimi. Wizualizacja tych jednostek jest widokiem dynamicznym w kodzie. Oznacza to, że można edytować typy w projektancie, a następnie zobaczyć modyfikacje odzwierciedlone w kodzie źródłowym jednostki. Podobnie Diagram klas jest zsynchronizowany ze zmianami wprowadzanymi w plikach kodu.

> [!NOTE]
> Jeśli projekt zawiera Diagram klas, a projekt odwołuje się do typu, który znajduje się w innym projekcie, Diagram klas nie pokazuje przywoływanego typu do czasu skompilowania projektu dla tego typu. Podobnie diagram nie wyświetla zmian w kodzie jednostki zewnętrznej do momentu odbudowania projektu dla tej jednostki.

## <a name="class-diagram-workflow"></a>Przepływ pracy diagramów klas

Diagramy klas mogą pomóc zrozumieć strukturę klasy projektów. Te projekty mogły zostać utworzone przez innych deweloperów lub wystarczy odświeżacz dla utworzonego projektu. Za pomocą diagramów klas można dostosowywać, udostępniać i prezentować informacje o projekcie innym osobom.

Pierwszym krokiem w przedprezentowaniu informacji o projekcie jest utworzenie diagramu klasy, który wyświetla elementy, które chcesz wyświetlić. Aby uzyskać więcej informacji, zobacz [Dodawanie diagramu klas](how-to-add-class-diagrams-to-projects.md). Można utworzyć wiele diagramów klas dla projektu, który może służyć do wyświetlania odrębnego widoku projektu, wybranego podzestawu typów projektu lub wybranego podzestawu elementów członkowskich typu.

Oprócz definiowania każdego diagramu klas, można również zmienić sposób przedstawiania informacji; Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md).

Po dostosowaniu co najmniej jednego diagramu klas można skopiować je do Microsoft Office dokumentów i wydrukować je lub wyeksportować jako pliki obrazów. Aby uzyskać więcej informacji, zobacz [jak: kopiowanie elementów diagramu klas do dokumentu Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [instrukcje: Drukowanie diagramów klas](how-to-print-class-diagrams.md) i [instrukcje: eksportowanie diagramów klas jako obrazów](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Projektant klas nie śledzi lokalizacji plików źródłowych, dlatego zmiana struktury projektu lub przeniesienie plików źródłowych w projekcie może spowodować, że Projektant klas utraci śledzenie tego typu, szczególnie typ źródłowy elementu typedef, klasy bazowe lub typy skojarzeń. Może zostać wyświetlony komunikat o błędzie, np. **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij ponownie zmodyfikowany lub zlokalizowany kod źródłowy do diagramu klas, aby go wyświetlić.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../writing-code-in-the-code-and-text-editor.md)
- [Zależności mapy w ramach rozwiązań](../../modeling/map-dependencies-across-your-solutions.md)
