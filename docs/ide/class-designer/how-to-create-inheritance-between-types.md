---
title: 'Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8060f17277a5e80a139ee8d6406fb40d0a84ec71
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915906"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Instrukcje: Tworzenie dziedziczenia między typami w Projektancie klas

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klasy przy użyciu **projektanta klas**, połączenie typu podstawowego z jego typu pochodnego lub typu. Może mieć relacji dziedziczenia między dwoma klasami, między klasą a interfejsem lub między dwa interfejsy.

## <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenia między typami

1.  Z projektu w **Eksploratora rozwiązań**, otwórz plik diagramu klasy (.cd).

     Jeśli nie masz diagram klas, należy go utworzyć. Zobacz [jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md).

2.  W **przybornika**w obszarze **projektanta klas**, kliknij przycisk **dziedziczenia**.

3.  Na diagramie klasy można narysować linię dziedziczenia między typami, które chcesz, zaczynając od:

    -   Klasy pochodnej do klasy bazowej

    -   Klasa implementująca zaimplementowanego interfejsu

    -   Rozszerzanie interfejsu do rozszerzonego interfejsu

4.  W przypadku typ pochodny od typu ogólnego, opcjonalnie kliknij przycisk linii dziedziczenia. W **właściwości** oknie **argumentów typu** właściwość będzie pasował do typu odpowiedniego dla typu ogólnego.

    > [!NOTE]
    > Jeśli klasa abstrakcyjna nadrzędny zawiera co najmniej jedną abstrakcyjną składową, wszystkie abstrakcyjne składowe są zaimplementowane jako nieabstrakcyjne klasy dziedziczące.
    >
    >  Mimo że można wizualizować istniejące typy rodzajowe, nie można utworzyć nowych typów rodzajowych. Ponadto nie można zmienić parametrów typu dla istniejących typów rodzajowych.

## <a name="see-also"></a>Zobacz także

- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Podstawowe informacje o dziedziczeniu](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Instrukcje: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)