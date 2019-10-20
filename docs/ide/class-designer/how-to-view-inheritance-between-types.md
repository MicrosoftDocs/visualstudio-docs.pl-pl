---
title: 'Porady: wyświetlanie dziedziczenia pomiędzy typami (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fd6d2ce365399550b5455ff8bf909e9cc56187b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647690"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Instrukcje: wyświetlanie dziedziczenia między typami w Projektant klas

Relację dziedziczenia można znaleźć, jeśli istnieje, między typem podstawowym a jego typami pochodnymi na diagramie klas w **Projektant klas**. Aby utworzyć relację dziedziczenia, jeśli nie istnieje, między dwoma typami, zobacz [How to: Create dziedziczenie między typami](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Aby znaleźć typ podstawowy

1. Na diagramie klas kliknij typ, dla którego chcesz zobaczyć klasę bazową lub interfejs.

2. W menu **Diagram klas** wybierz **Pokaż klasę bazową** lub **Pokaż interfejsy podstawowe**.

     Na diagramie zostanie wybrana Klasa bazowa lub interfejs typu. Wszystkie ukryte linie dziedziczenia są teraz widoczne między dwoma kształtami.

Możesz również kliknąć prawym przyciskiem myszy typ, którego typ podstawowy chcesz wyświetlić, a następnie wybierz polecenie **Pokaż klasę bazową** lub **Pokaż interfejsy podstawowe**.

## <a name="to-find-the-derived-types"></a>Aby znaleźć typy pochodne

1. Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klasy pochodne lub interfejsy.

2. W menu **Diagram klas** wybierz pozycję **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

     Klasy pochodne lub interfejsy są wyświetlane na diagramie. Wszystkie ukryte linie dziedziczenia są teraz wyświetlane między kształtami.

Możesz również kliknąć prawym przyciskiem myszy typ, dla którego chcesz zobaczyć typy pochodne, a następnie wybrać **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)