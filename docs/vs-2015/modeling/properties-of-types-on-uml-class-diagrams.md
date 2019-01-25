---
title: Właściwości typów w UML, diagramy klas | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 520843ee596e67de5d4e804e90302f931a1d3b57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803407"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Właściwości typów w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML *typu* jest klasą, interfejsem lub wyliczenia.  
  
> [!NOTE]
>  Ten temat dotyczy właściwościom typów w diagramach przypadków UML. Więcej informacji znajduje się w następujących tematach:  
  
-   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Właściwości operacji w diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [Właściwości skojarzeń w diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Właściwości  
 Są to właściwości klasą, interfejsem lub wyliczenia.  
  
 Aby wyświetlić właściwości typu, kliknij prawym przyciskiem myszy typu na diagramie lub w **Eksploratora modelu UML**, a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  
  
|**Property**|**Default**|Pojawia się w|Opis|  
|------------------|-----------------|----------------|-----------------|  
|**Nazwa**|Domyślna nazwa|Wszystkie elementy|Identyfikuje element.|  
|**Kwalifikowana nazwa**|Zawierającego pakiet:: Nazwa typu|Wszystkie elementy|Jednoznacznie identyfikuje element. Prefiks kwalifikowaną nazwę pakietu, który go zawiera.|  
|**Kolor**|Domyślne dla rodzaju typu|Wszystkie elementy|Kolor tego kształtu. W przeciwieństwie do innych właściwości to nie jest właściwością bazowego elementu modelu. Różne widoki tego samego typu mogą mieć różnych kolorach.|  
|**Jest abstrakcyjna**|False|Class|W przypadku opcji true klasy nie można utworzyć wystąpienia i jest przeznaczona do użytku jako klasę bazową.|  
|**Jest typu liść**|False|Klasa, interfejs|W przypadku opcji true typ nie jest przeznaczona do ma typy pochodne.|  
|**Jest aktywny**|False|Class|W przypadku opcji true każde wystąpienie tego typu jest skojarzony z wątkiem kontrolki.|  
|**Widoczność**|Public|Klasy, interfejsu, wyliczenie|-Public - widoczne globalnie.<br />— Prywatny — ten typ jest widoczny w pakiecie, który jest jego właścicielem.<br />-Package - widoczne w pakiecie.|  
|**Elementy robocze**|skojarzone 0|Wszystkie elementy|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Opis**|(pusty)|Wszystkie elementy|Można wprowadzić ogólne uwagi dotyczące elementu w tym miejscu.|  
|**Powiązanie szablonu**|(Brak)|Klasy, interfejsu, wyliczenie|Jeśli nie jest pusta, tego typu zdefiniowanego przez powiązanie wartości parametrów do tej klasy szablonu. Rozwiń właściwość, aby zobaczyć powiązania parametrów szablonu.|  
|**Parametry szablonu**|(Brak)|Klasy, interfejsu, wyliczenie|Jeśli nie jest pusta, jest klasą szablonu, który ma następujące parametry wymienione w tym miejscu. Aby dodać parametry lub wyświetlić właściwości poszczególne parametry, kliknij **[...]** .|  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości atrybutów w diagramach przypadków UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Właściwości operacji w diagramach przypadków UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Właściwości skojarzeń w diagramach przypadków UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)
