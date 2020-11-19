---
title: 'Porady: implementowanie interfejsu (Projektant klas)'
description: Dowiedz się, jak zaimplementować interfejs na diagramie klas, łącząc go z klasą, która dostarcza kod dla metod interfejsu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad038774b4acfb7256edbaa35ae4c67cfe835891
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901378"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Instrukcje: implementowanie interfejsu w Projektant klas

W **Projektant klas** można zaimplementować interfejs na diagramie klas, łącząc go z klasą, która dostarcza kod dla metod interfejsu. **Projektant klas** generuje implementację interfejsu i wyświetla relacje między interfejsem a klasą jako relację dziedziczenia. Interfejs można zaimplementować, rysując linię dziedziczenia między interfejsem a klasą lub przeciągając interfejs z Widok klasy.

> [!TIP]
> Interfejsy można tworzyć w taki sam sposób, jak w przypadku innych typów. Jeśli interfejs istnieje, ale nie jest wyświetlany na diagramie klas, należy najpierw go wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typów przy użyciu Projektant klas](how-to-create-types.md) i [instrukcje: wyświetlanie istniejących typów](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs poprzez rysowanie linii dziedziczenia

1. Na diagramie klasy Wyświetl interfejs i klasę, która będzie implementować interfejs.

2. Narysuj linię dziedziczenia z klasy i interfejsu.

     Do klasy jest dołączona lizak, a etykieta o nazwie interfejsu identyfikuje relację dziedziczenia. Program Visual Studio generuje klasy pośredniczące dla wszystkich elementów członkowskich interfejsu.

Aby uzyskać więcej informacji, zobacz [jak: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs z okna Widok klasy

1. Na diagramie klas Wyświetl klasę, w której chcesz zaimplementować interfejs.

2. Otwórz **Widok klasy** i Znajdź interfejs.

    > [!TIP]
    > Jeśli **Widok klasy** nie jest otwarty, Otwórz **Widok klasy** z menu **Widok** lub naciśnij **klawisze CTRL** + **SHIFT** + **C**.

3. Przeciągnij węzeł interfejsu do kształtu klasy na diagramie.

     Do klasy jest dołączona lizak, a etykieta o nazwie interfejsu identyfikuje relację dziedziczenia. Program Visual Studio generuje klasy pośredniczące dla wszystkich elementów członkowskich interfejsu; w tym momencie interfejs jest zaimplementowany.

## <a name="see-also"></a>Zobacz także

- [Porady: tworzenie typów za pomocą Projektanta klas](how-to-create-types.md)
- [Instrukcje: wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Instrukcje: Tworzenie dziedziczenia między typami](how-to-create-inheritance-between-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)
