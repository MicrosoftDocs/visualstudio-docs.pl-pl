---
title: 'Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas) | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 80d4ebe992a3406a4e8c54b033cd4f526335231b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416975"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Instrukcje: Tworzenie dziedziczenia między typami (Projektant klas) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klasy przy użyciu projektanta klas, połączyć z typu podstawowego z jego typu pochodnego lub typów. Może mieć relacji dziedziczenia między dwoma klasami, między klasą a interfejsem lub między dwa interfejsy.  
  
### <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenia między typami  
  
1. Z projektu w Eksploratorze rozwiązań Otwórz plik diagramu klasy (.cd).  
  
     Jeśli nie masz diagram klas, należy go utworzyć. Zobacz [jak: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2. W **przybornika**w obszarze **projektanta klas**, kliknij przycisk **dziedziczenia**.  
  
3. Na diagramie klasy można narysować linię dziedziczenia między typami, które chcesz, zaczynając od:  
  
    - Klasy pochodnej do klasy bazowej  
  
    - Klasa implementująca zaimplementowanego interfejsu  
  
    - Rozszerzanie interfejsu do rozszerzonego interfejsu  
  
4. W przypadku typ pochodny od typu ogólnego, opcjonalnie kliknij przycisk linii dziedziczenia. W **właściwości** oknie **argumentów typu** właściwość będzie pasował do typu odpowiedniego dla typu ogólnego.  
  
    > [!NOTE]
    > Jeśli klasa abstrakcyjna nadrzędny zawiera co najmniej jedną abstrakcyjną składową, wszystkie abstrakcyjne składowe są zaimplementowane jako nieabstrakcyjne klasy dziedziczące.   
    >   
    >  Mimo że można wizualizować istniejące typy rodzajowe, nie można utworzyć nowych typów rodzajowych. Ponadto nie można zmienić parametrów typu dla istniejących typów rodzajowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dziedziczenie](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Podstawowe informacje o dziedziczeniu](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Instrukcje: Wyświetlanie dziedziczenia między typami (Projektant klas)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Klasy Visual C++ w Projektancie klas](../ide/visual-cpp-classes-in-class-designer.md)
