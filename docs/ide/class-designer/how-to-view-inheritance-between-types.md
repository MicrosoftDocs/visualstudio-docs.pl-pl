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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ac6987c671f99c70a0c4cc7e2b407e0db17f54c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951018"
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