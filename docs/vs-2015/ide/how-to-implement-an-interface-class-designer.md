---
title: 'Instrukcje: Implementowanie interfejsu (Projektant klas) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b437fb34902783002baedee992a21ee61a86c2e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685625"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Instrukcje: Implementowanie interfejsu (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektancie klas można zaimplementować interfejsu na diagramie klas, łącząc je do klasy, która zawiera kod dla metody interfejsu. Projektant klas generuje implementację interfejsu i wyświetla relacji między interfejsem i klasy jako relacji dziedziczenia. Można zaimplementować interfejs, za pomocą rysowania linii dziedziczenia między interfejsem i klasy lub przeciągnąć interfejs z widoku klasy.  
  
> [!TIP]
> Można utworzyć taki sam sposób utworzyć inne typy interfejsów. Jeśli interfejs istnieje, ale nie jest wyświetlane na diagramie klasy, następnie najpierw wyświetlamy go. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typów za pomocą projektanta klas](../ide/how-to-create-types-by-using-class-designer.md) i [jak: Wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs, za pomocą rysowania linię dziedziczenia  
  
1. Na diagramie klas wyświetlić interfejs i klasa, która będzie implementować interfejs.  
  
2. Rysuj linię dziedziczenia z klasy i interfejsu.  
  
    Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu.  
  
   Aby uzyskać więcej informacji, zobacz [jak: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs w oknie widoku klas  
  
1. Na diagramie klasy można wyświetlić klasę, która ma zostać zaimplementowany interfejs.  
  
2. Otwórz widok klas i wyszukaj interfejs.  
  
    > [!TIP]
    > Jeśli widok klas nie jest otwarty, otwórz widok klas z **widoku** menu. Aby uzyskać więcej informacji dotyczących widoku klas, zobacz [Viewing Classes and Their Members](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3. Przeciągnij węzeł interfejsu klasa kształt na diagramie.  
  
     Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu; w tym momencie interfejs jest implementowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie typów za pomocą projektanta klas](../ide/how-to-create-types-by-using-class-designer.md)   
 [Instrukcje: Wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md)   
 [Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refaktoryzacja klas i typów (Projektant klas)](../ide/refactoring-classes-and-types-class-designer.md)
