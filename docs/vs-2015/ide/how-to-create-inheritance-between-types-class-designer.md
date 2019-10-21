---
title: 'Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668105"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klasy przy użyciu Projektant klas, Połącz typ podstawowy z typem pochodnym lub typami. Istnieje relacja dziedziczenia między dwiema klasami, między klasą a interfejsem lub między dwoma interfejsami.

### <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenie między typami

1. Z projektu w Eksplorator rozwiązań otwórz plik diagramu klasy (. CD).

     Jeśli nie masz diagramu klas, utwórz go. Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

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

## <a name="see-also"></a>Zobacz też
 [Dziedziczenie](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) dziedziczenia [podstawowe informacje](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) [na temat sposobu: wyświetlania dziedziczenia między typami (Projektant klas)](../ide/how-to-view-inheritance-between-types-class-designer.md) [klasy wizualnej C++ w Projektant klas](../ide/visual-cpp-classes-in-class-designer.md)
