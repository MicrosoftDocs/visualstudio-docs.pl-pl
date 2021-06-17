---
title: Używanie Projektant klas
description: Dowiedz się, jak projektować, wizualizować i refaktoryzować klasy i inne typy w kodzie za pomocą Projektant klas w Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85921343ac52c066735d607ce32635e953cf2e6a
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254783"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Projektowanie i wyświetlanie klas i typów za pomocą Projektant klas

Projektowanie, wizualizowanie i refaktoryzacja klas i innych typów w kodzie przy **użyciu Projektant klas** w Visual Studio. Diagramy klas są służące do tworzenia i edytowania klas w projekcie języka C#, Visual Basic lub C++. Możesz również użyć diagramów klas, aby lepiej zrozumieć strukturę projektu lub zreorganizować kod.

>[!NOTE]
>Projektant klas nie jest dostępna w projektach .NET Core.

## <a name="what-you-can-do-with-class-diagrams"></a>Co można zrobić za pomocą diagramów klas

- **Projektowanie:** Edytuj kod projektu, edytując diagram klas. Dodaj nowe elementy i usuń niechciane elementy. Zmiany zostaną odzwierciedlone w kodzie.

- **Wizualizacja:** Poznaj strukturę projektu, wyświetlając klasy w projekcie na diagramie. Dostosuj diagram, aby można było skupić się na szczegółach projektu, na których zależy Ci najbardziej. Zapisz diagram, aby użyć go później na pokaz lub dokumentację.

- **Refaktoryzacja:** przesłaniaj metody, zmieniaj nazwy identyfikatorów, refaktoryzuj parametry oraz implementuj interfejsy i klasy abstrakcyjne.

## <a name="view-types-and-relationships"></a>Wyświetlanie typów i relacji

Diagramy klas pokazują szczegóły typów, na przykład ich składowe składowe i relacje między nimi. Wizualizacja tych jednostek jest dynamicznym widokiem kodu. Oznacza to, że możesz edytować typy w projektancie, a następnie zobaczyć zmiany odzwierciedlone w kodzie źródłowym jednostki. Podobnie diagram klas jest zsynchronizowany ze zmianami wprowadzonymi w plikach kodu.

> [!NOTE]
> Jeśli projekt zawiera diagram klas, a projekt odwołuje się do typu znajdującego się w innym projekcie, diagram klas nie pokazuje typu, do których się odwołujesz, dopóki nie skompilowasz projektu dla tego typu. Podobnie diagram nie wyświetla zmian w kodzie jednostki zewnętrznej do momentu ponownego skompilowania projektu dla tej jednostki.

## <a name="class-diagram-workflow"></a>Przepływ pracy diagramu klas

Diagramy klas mogą ułatwić zrozumienie struktury klas projektów. Te projekty mogły zostać utworzone przez innych deweloperów lub wystarczy odświeżyć projekt utworzony samodzielnie. Za pomocą diagramów klas można dostosowywać, udostępniać i prezentować informacje o projekcie innym osobom.

Pierwszym krokiem prezentowania informacji o projekcie jest utworzenie diagramu klasy, który wyświetla to, co chcesz pokazać. Aby uzyskać więcej informacji, zobacz [Dodawanie diagramu klasy](how-to-add-class-diagrams-to-projects.md). Dla projektu można utworzyć wiele diagramów klas, które mogą służyć do wyświetlania odrębnego widoku projektu, wybranego podzestawu typów projektu lub wybranego podzestawu składowych typów.

Oprócz definiowania tego, co pokazuje każdy diagram klas, można również zmienić sposób prezentowania informacji; Aby uzyskać więcej informacji, [zobacz How to: Customize class diagrams](how-to-customize-class-diagrams.md)( Jak dostosować diagramy klas).

Po dostrojeniu co najmniej jednego diagramu klasy możesz skopiować go do dokumentów Microsoft Office wydrukować lub wyeksportować jako pliki obrazów. Aby uzyskać więcej informacji, zobacz How [to: Copy class diagram elements to a Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md)document ,How [to: Print class diagrams](how-to-print-class-diagrams.md) and How to: Export class diagrams as images (Jak drukować diagramy klas) i [How to: Export class diagrams as images](how-to-export-class-diagrams-as-images.md)(Jak eksportować diagramy klas jako obrazy).

> [!NOTE]
> Projektant klas nie śledzi lokalizacji plików źródłowych, więc zmiana struktury projektu lub przeniesienie plików źródłowych w projekcie może spowodować utratę śledzenia typu przez program Projektant klas, w szczególności typu źródłowego typedef, klas bazowych lub typów skojarzenia. Może wystąpić błąd, na przykład Projektant klas **nie może wyświetlić tego typu .** Jeśli to zrobisz, przeciągnij zmodyfikowany lub przeniesiony kod źródłowy ponownie do diagramu klas, aby ponownie go ominić.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../writing-code-in-the-code-and-text-editor.md)
- [Zależności mapy w ramach rozwiązań](../../modeling/map-dependencies-across-your-solutions.md)
