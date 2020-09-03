---
title: 'Instrukcje: implementowanie interfejsu (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b750830e8263d0016f52a71ad4eac8c6950eda8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651863"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Porady: implementowanie interfejsu (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektant klas można zaimplementować interfejs na diagramie klas, łącząc go z klasą, która dostarcza kod dla metod interfejsu. Projektant klas generuje implementację interfejsu i wyświetla relacje między interfejsem a klasą jako relację dziedziczenia. Interfejs można zaimplementować, rysując linię dziedziczenia między interfejsem a klasą lub przeciągając interfejs z Widok klasy.

> [!TIP]
> Interfejsy można tworzyć w taki sam sposób, jak w przypadku innych typów. Jeśli interfejs istnieje, ale nie jest wyświetlany na diagramie klas, należy najpierw go wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typów przy użyciu Projektant klas](../ide/how-to-create-types-by-using-class-designer.md) i [instrukcje: wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md).

### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs poprzez rysowanie linii dziedziczenia

1. Na diagramie klasy Wyświetl interfejs i klasę, która będzie implementować interfejs.

2. Narysuj linię dziedziczenia z klasy i interfejsu.

    Do klasy jest dołączona lizak, a etykieta o nazwie interfejsu identyfikuje relację dziedziczenia. Program Visual Studio generuje klasy pośredniczące dla wszystkich elementów członkowskich interfejsu.

   Aby uzyskać więcej informacji, zobacz [jak: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs z okna Widok klasy

1. Na diagramie klas Wyświetl klasę, w której chcesz zaimplementować interfejs.

2. Otwórz Widok klasy i Znajdź interfejs.

    > [!TIP]
    > Jeśli Widok klasy nie jest otwarty, Otwórz Widok klasy z menu **Widok** . Aby uzyskać więcej informacji na temat Widok klasy, zobacz [przeglądanie klas i ich członków](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

3. Przeciągnij węzeł interfejsu do kształtu klasy na diagramie.

     Do klasy jest dołączona lizak, a etykieta o nazwie interfejsu identyfikuje relację dziedziczenia. Program Visual Studio generuje klasy pośredniczące dla wszystkich elementów członkowskich interfejsu; w tym momencie interfejs jest zaimplementowany.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie typów za pomocą Projektant klas](../ide/how-to-create-types-by-using-class-designer.md) [instrukcje: wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md) [instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md) [klasy refaktoryzacji i typy (Projektant klas)](../ide/refactoring-classes-and-types-class-designer.md)
