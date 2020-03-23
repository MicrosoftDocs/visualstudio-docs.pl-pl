---
title: 'Porady: implementowanie interfejsu (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe8db6c6bd7df5285880f7f860df5bb26db736a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590114"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Jak: Implementowanie interfejsu w Projektancie klas

W **projektancie klas**można zaimplementować interfejs na diagramie klasy, łącząc go z klasą, która udostępnia kod dla metod interfejsu. **Class Designer** generuje implementację interfejsu i wyświetla relację między interfejsem a klasą jako relację dziedziczenia. Interfejs można zaimplementować, rysując linię dziedziczenia między interfejsem a klasą lub przeciągając interfejs z widoku klasy.

> [!TIP]
> Interfejsy można tworzyć w taki sam sposób, jak inne typy. Jeśli interfejs istnieje, ale nie pojawia się na diagramie klasy, a następnie najpierw go wyświetlić. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie typów przy użyciu Projektanta klas](how-to-create-types.md) i [jak: Wyświetlanie istniejących typów](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs przez rysowanie linii dziedziczenia

1. Na diagramie klasy wyświetl interfejs i klasę, która zaimplementuje interfejs.

2. Narysuj linię dziedziczenia z klasy i interfejsu.

     Lizak pojawia się dołączony do klasy i etykieta z nazwą interfejsu identyfikuje relację dziedziczenia. Visual Studio generuje wycinki dla wszystkich elementów członkowskich interfejsu.

Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs z okna Widok klasy

1. Na diagramie klasy wyświetl klasę, która ma zaimplementować interfejs.

2. Otwórz **widok klasy** i znajdź interfejs.

    > [!TIP]
    > Jeśli **widok klasy** nie jest otwarty, otwórz widok **klasy** z menu **Widok** lub naciśnij klawisz **Ctrl**+**Shift**+**C**.

3. Przeciągnij węzeł interfejsu do kształtu klasy na diagramie.

     Lizak pojawia się dołączony do klasy i etykieta z nazwą interfejsu identyfikuje relację dziedziczenia. Visual Studio generuje wycinki dla wszystkich elementów członkowskich interfejsu; w tym momencie interfejs jest zaimplementowany.

## <a name="see-also"></a>Zobacz też

- [Porady: tworzenie typów za pomocą Projektanta klas](how-to-create-types.md)
- [Jak: Wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)
