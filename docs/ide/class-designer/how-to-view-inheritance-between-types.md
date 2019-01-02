---
title: 'Instrukcje: Wyświetlanie dziedziczenia między typami (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9da919b2a3ead6ab48d199e9370c799afb9f9a65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925436"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Instrukcje: Wyświetlanie dziedziczenia między typami w Projektancie klas

Można znaleźć relacji dziedziczenia, jeśli istnieje między typem podstawowym i jego typów pochodnych na diagramie klasy w **projektanta klas**. Aby utworzyć relację dziedziczenia, jeśli nie istnieją między dwoma typami, zobacz [jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Aby znaleźć typ podstawowy

1.  Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klasy bazowej lub interfejsu.

2.  Na **Diagram klas** menu, wybierz **Pokaż klasy podstawowe** lub **Pokaż interfejsy Base**.

     Typ klasy bazowej lub interfejsu widoczny jako zaznaczony na diagramie. Wszystkie linie dziedziczenia ukryte pojawiają się między dwoma kształtami.

Również kliknięciu prawym przyciskiem myszy typ, którego typ podstawowy, które chcesz wyświetlić, a następnie wybierz **Pokaż klasy bazowej** lub **Pokaż interfejsy podstawowe**.

## <a name="to-find-the-derived-types"></a>Aby znaleźć typy pochodne

1.  Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klas pochodnych lub interfejsów.

2.  Na **Diagram klas** menu, wybierz **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

     Klasy pochodne typu lub interfejsy są wyświetlane na diagramie. Wszystkie linie dziedziczenia ukryte pojawiają się między kształtów.

Również kliknięciu prawym przyciskiem myszy typ, dla którego chcesz wyświetlić jego typów pochodnych, a następnie wybierz **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)