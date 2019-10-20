---
title: Właściwości typów w diagramach klas UML | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671320"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Właściwości typów w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W diagramie klas UML *Typ* jest klasą, interfejsem lub wyliczeniem.

> [!NOTE]
> Ten temat zawiera informacje o właściwościach typów w diagramach klas UML. Więcej informacji znajduje się w następujących tematach:

- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

- [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Właściwości operacji w diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Właściwości skojarzeń w diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Właściwości
 Są to właściwości klasy, interfejsu lub wyliczenia.

 Aby wyświetlić właściwości typu, kliknij prawym przyciskiem myszy typ na diagramie lub w **Eksploratorze modelu UML**, a następnie kliknij polecenie **Właściwości**. Właściwości są wyświetlane w oknie **Właściwości** .

|**Wartość**|**Default**|Pojawia się w|Opis|
|------------------|-----------------|----------------|-----------------|
|**Nazwa**|Nazwa domyślna|Wszystkie elementy|Identyfikuje element.|
|**Kwalifikowana nazwa**|Zawierający pakiet:: type name|Wszystkie elementy|Jednoznacznie identyfikuje element. Poprzedzona nazwą kwalifikowaną pakietu, która go zawiera.|
|**Kolor**|Wartość domyślna dla rodzaju typu|Wszystkie elementy|Kolor tego kształtu. W przeciwieństwie do innych właściwości, nie jest to właściwość bazowego elementu modelu. Różne widoki tego samego typu mogą mieć różne kolory.|
|**Jest abstrakcyjny**|False|Class|Jeśli wartość jest równa true, nie można utworzyć wystąpienia klasy i jest przeznaczona do użycia jako klasa bazowa.|
|**Jest liściem**|False|Klasa, interfejs|W przypadku wartości true typ nie jest przeznaczony dla typów pochodnych.|
|**Jest aktywny**|False|Class|W przypadku wartości true każde wystąpienie tego typu jest skojarzone z wątkiem kontrolki.|
|**Propagowan**|Public|Klasa, interfejs, Wyliczenie|-Public-globalnie widoczne.<br />-Private — ten typ jest widoczny w pakiecie, który jest jego właścicielem.<br />-Pakiet widoczny w pakiecie.|
|**Elementy robocze**|0 skojarzone|Wszystkie elementy|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Opis**|puste|Wszystkie elementy|Tutaj możesz tworzyć ogólne uwagi na temat tego elementu.|
|**Powiązanie szablonu**|dawaj|Klasa, interfejs, Wyliczenie|Jeśli nie jest pusty, ten typ jest definiowany przez powiązanie wartości parametrów z tą klasą szablonu. Rozwiń właściwość, aby wyświetlić powiązania parametrów szablonu.|
|**Parametry szablonu**|dawaj|Klasa, interfejs, Wyliczenie|Jeśli nie jest pusty, jest to Klasa szablonu, która zawiera parametry wymienione w tym miejscu. Aby dodać parametry lub wyświetlić właściwości poszczególnych parametrów, kliknij **[...]** .|

## <a name="see-also"></a>Zobacz też
 [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) — [właściwości operacji na diagramach](../modeling/properties-of-operations-on-uml-class-diagrams.md) klas UML [właściwości skojarzenia na](../modeling/properties-of-associations-on-uml-class-diagrams.md) diagramach klas UML [diagramy: wytyczne](../modeling/uml-class-diagrams-guidelines.md)
