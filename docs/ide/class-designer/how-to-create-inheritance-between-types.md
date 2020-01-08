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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590374"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Instrukcje: Tworzenie dziedziczenia między typami w Projektant klas

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klasy przy użyciu **Projektant klas**, Połącz typ podstawowy z typem pochodnym lub typami. Istnieje relacja dziedziczenia między dwiema klasami, między klasą a interfejsem lub między dwoma interfejsami.

## <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenie między typami

1. Z projektu w **Eksplorator rozwiązań**Otwórz plik diagramu klasy (. CD).

     Jeśli nie masz diagramu klas, utwórz go. Zobacz [jak: dodać diagramy klas do projektów](how-to-add-class-diagrams-to-projects.md).

2. W **przyborniku**w obszarze **Projektant klas**kliknij pozycję **dziedziczenie**.

3. Na diagramie klasy należy narysować linię dziedziczenia między typami, które chcesz, zaczynając od:

    - Klasa pochodna klasy bazowej

    - Implementacja klasy do zaimplementowanego interfejsu

    - Rozszerzanie interfejsu do rozszerzonego interfejsu

4. Opcjonalnie, jeśli masz typ pochodny z typu ogólnego, kliknij linię dziedziczenia. W oknie **Właściwości** ustaw właściwość **argumenty typu** tak, aby odpowiadała typowi dla typu ogólnego.

    > [!NOTE]
    > Jeśli nadrzędna Klasa abstrakcyjna zawiera co najmniej jeden abstrakcyjny element członkowski, wszystkie abstrakcyjne składowe są implementowane jako nieabstrakcyjne klasy dziedziczenia.
    >
    >  Chociaż można wizualizować istniejące typy ogólne, nie można tworzyć nowych typów ogólnych. Nie można również zmienić parametrów typu dla istniejących typów ogólnych.

## <a name="see-also"></a>Zobacz także

- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Podstawowe informacje o dziedziczeniu](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Instrukcje: wyświetlanie dziedziczenia między typami](how-to-view-inheritance-between-types.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)
