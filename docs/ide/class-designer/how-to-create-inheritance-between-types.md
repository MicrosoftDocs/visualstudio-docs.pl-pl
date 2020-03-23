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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf540056318e092db13521dc80478cc7eb91948
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590374"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Jak: Tworzenie dziedziczenia między typami w Projektancie klas

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klas przy użyciu **projektanta klas,** należy połączyć typ podstawowy z jego typem pochodnym lub typami. Relacja dziedziczenia między dwiema klasami, między klasą a interfejsem lub między dwoma interfejsami.

## <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenie między typami

1. Z projektu w **Eksploratorze rozwiązań**otwórz plik diagramu klasy (cd).

     Jeśli nie masz diagramu klas, utwórz go. Zobacz [Jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md).

2. W **przyborniku**w obszarze **Projektant klas**kliknij pozycję **Dziedziczenie**.

3. Na diagramie klas narysuj linię dziedziczenia między typami, które chcesz, zaczynając od:

    - Klasa pochodna do klasy podstawowej

    - Klasa implementująca do zaimplementowanego interfejsu

    - Rozszerzający interfejs do rozszerzonego interfejsu

4. Opcjonalnie, jeśli masz typ pochodny z typu ogólnego, kliknij wiersz dziedziczenia. W oknie **Właściwości** ustaw właściwość **Typ argumenty,** aby dopasować typ, który ma dla typu ogólnego.

    > [!NOTE]
    > Jeśli nadrzędna klasa abstrakcyjna zawiera co najmniej jeden abstrakcyjny element członkowski, wszystkie abstrakcyjne elementy członkowskie są implementowane jako niesetrakcyjne klasy dziedziczenia.
    >
    >  Chociaż można wizualizować istniejące typy ogólne, nie można tworzyć nowych typów ogólnych. Nie można również zmienić parametrów typu dla istniejących typów ogólnych.

## <a name="see-also"></a>Zobacz też

- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Podstawowe informacje o dziedziczeniu](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Jak: Wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)
