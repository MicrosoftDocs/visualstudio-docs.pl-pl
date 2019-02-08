---
title: Używaj projektanta klas
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee4910471693a2941ec9548773a2f50e443a639b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910743"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Projektowanie i wyświetlanie klas i typów za pomocą projektanta klas

Projektowanie oraz ich wizualizowanie i Refaktoryzacja klas i innych typów w kodzie za pomocą **projektanta klas** w programie Visual Studio. Użyj diagramów klas do tworzenia i edytowania klas w swojej C#, Visual Basic lub C++ projektu. Diagramy klas umożliwia również do struktury projektu, lepiej zrozumieć lub przeorganizować swój kod.

## <a name="what-you-can-do-with-class-diagrams"></a>Co można zrobić za pomocą diagramów klas

- **Projekt**: Edytowanie kodu projektu poprzez edycję diagramu klas. Dodawanie nowych elementów i usuń niepożądane. Zmiany są odzwierciedlane w kodzie.

- **Wizualizuj**: Zrozumienie struktury projektu, wyświetlając klasy w projekcie na diagramie. Dostosuj do diagramu, dzięki czemu można skupić się na potrzeby szczegółów projektu, które najbardziej interesujących Cię. Zapisz diagramu do późniejszego użycia w celu wykazania lub dokumentacji.

- **Refaktoryzuj**: Przesłaniaj metody i zmiana nazw identyfikatorów, Refaktoryzacja parametrów, implementowanie interfejsów i klas abstrakcyjnych.

## <a name="view-types-and-relationships"></a>Wyświetlanie typów i relacji

Diagramy klas wyświetlenie szczegółów dotyczących typów, na przykład ich składowe i relacje między nimi. Wizualizacja te jednostki jest dynamiczny widok w kodzie. Oznacza to, że można edytować typy w Projektancie i następnie zobacz zmiany zostaną uwzględnione w kodzie źródłowym jednostki. Podobnie diagram klas jest synchronizowana z zmiany wprowadzone do plików kodu.

> [!NOTE]
> Jeśli projekt zawiera diagram klas i projekt odwołuje się do typu, który znajduje się w innym projekcie, diagram klas nie są wyświetlane odwołanie typu do czasu kompilowania projektu dla tego typu. Podobnie diagram nie są wyświetlane zmiany do kodu zewnętrznej jednostki dopóki można ponownie skompilować projekt dla danej jednostki.

## <a name="class-diagram-workflow"></a>Klasa diagram przepływu pracy

Diagramy klas mogą pomóc zrozumieć struktura klas projektów. Te projekty został utworzony przez innych programistów lub po prostu potrzebujesz przypomnienia informacji na temat projektu, utworzonych przez siebie. Diagramy klas służy do dostosowywania, udostępnianie i prezentować informacje o projekcie z innymi osobami.

Pierwszym etapem prezentowanie informacji o projekcie jest utworzyć diagram klas, który wyświetla mają być wyświetlane. Aby uzyskać więcej informacji, zobacz [Dodaj diagram klas](how-to-add-class-diagrams-to-projects.md). Możesz utworzyć wiele diagramów klas do projektu, który może służyć do wyświetlania różnych widoku projektu, wybrany podzbiór typów projektów lub wybrany podzbiór elementów członkowskich typów.

Oprócz definiowania, co pokazuje każdy diagram klas, możesz również zmienić sposób, w jaki informacje są prezentowane; Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie diagramów klas](how-to-customize-class-diagrams.md).

Po mają dostosowaniu jeden lub więcej diagramów klas, możesz skopiować je do dokumentów programu Microsoft Office i drukowanie lub wyeksportować je jako pliki obrazów. Aby uzyskać więcej informacji, zobacz [jak: Kopiowanie elementów diagramu klas do dokumentu pakietu Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [jak: Drukowanie diagramów klas](how-to-print-class-diagrams.md) i [jak: Eksportowanie diagramów klas jako obrazów](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Projektant klas nie śledzi lokalizację plików źródłowych, więc zmiany do struktury projektu, lub przenoszenia plików źródłowych w projekcie może spowodować projektanta klas, utratę informacji typu, szczególnie typ źródła typedef, klasy bazowe lub typu powiązania. Możesz otrzymać błąd, takich jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przenoszone do diagramu klas, aby ją wyświetlić ją ponownie.

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../writing-code-in-the-code-and-text-editor.md)
- [Zależności mapy w ramach rozwiązań](../../modeling/map-dependencies-across-your-solutions.md)