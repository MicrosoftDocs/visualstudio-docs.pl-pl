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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47907493451841b631d561bfddb74676a460ff29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591778"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Jak: Wyświetlanie dziedziczenia między typami w Projektancie klas

Relację dziedziczenia, jeśli istnieje, między typem podstawowym a jego typami pochodnymi można znaleźć na diagramie klasy w **projektancie klas**. Aby utworzyć relację dziedziczenia, jeśli nie istnieje, między dwoma typami, zobacz [Jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Aby znaleźć typ podstawowy

1. Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klasę podstawową lub interfejs.

2. W menu **Diagram klas** wybierz polecenie Pokaż **klasę podstawową** lub **Pokaż interfejsy podstawowe**.

     Klasa podstawowa lub interfejs typu pojawi się zaznaczona na diagramie. Wszystkie ukryte linie dziedziczenia są teraz wyświetlane między dwoma kształtami.

Można również kliknąć prawym przyciskiem myszy typ, którego typ podstawowy ma być wyświetlany, a następnie wybrać pozycję **Pokaż klasę podstawową** lub **Pokaż interfejsy podstawowe**.

## <a name="to-find-the-derived-types"></a>Aby znaleźć typy pochodne

1. Na diagramie klas kliknij typ, dla którego chcesz zobaczyć pochodne klasy lub interfejsy.

2. W menu **Diagram klas** wybierz polecenie Pokaż **klasy pochodne** lub **Pokaż interfejsy pochodne**.

     Klasy pochodne typu lub interfejsy pojawiają się na diagramie. Między kształtami są teraz wyświetlane wszystkie ukryte linie dziedziczenia.

Można również kliknąć prawym przyciskiem myszy typ, dla którego mają być wyświetlane jego typy pochodne, a następnie wybrać polecenie **Pokaż klasy pochodne** lub **Pokaż interfejsy pochodne**.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
