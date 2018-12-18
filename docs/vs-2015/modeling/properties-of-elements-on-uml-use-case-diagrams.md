---
title: Właściwości elementów na UML, diagramy przypadków użycia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a81f7630a1a903af2f9c21aee3249ea6fe156af2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762824"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Właściwości elementów na diagramach przypadków użycia UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie przypadków użycia UML każdego elementu na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratora modelu UML** a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  
  
> [!NOTE]
>  Ten temat dotyczy właściwości elementów w diagramach przypadków użycia UML. Aby uzyskać więcej informacji o tym, jak odczytać diagramy aktywności UML, zobacz [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md). Aby uzyskać więcej informacji na temat narysować diagramy aktywności UML, zobacz [diagramy przypadków użycia UML: wskazówki dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Właściwości elementów  
  
|Właściwość|Domyślny|Element|Opis|  
|--------------|-------------|-------------|-----------------|  
|**Nazwa**|Domyślna nazwa|Wszystkie|Identyfikuje element.|  
|**Kwalifikowana nazwa**|Pakiet:: nazwy|Wszystkie|Jednoznacznie identyfikuje element. Prefiks kwalifikowaną nazwę pakietu, który go zawiera.|  
|**Elementy robocze**|skojarzone 0|Wszystkie|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Opis**|(Brak)|Wszystkie|Można wprowadzić ogólne uwagi na temat elementu, w tym miejscu.|  
|**Kolor**|(ustawienie domyślne)|Wszystkie|Kolor kształtu. W przeciwieństwie do innych właściwości, to nie jest właściwością elementu, który wyświetla kształtu.|  
|**Ścieżka obrazu**|(Brak)|aktora|Ścieżka pliku obrazu, które mają być używane zamiast domyślnej ikony aktora. Ikona powinna być plik zasobów w ramach projektu programu Visual Studio.|  
|**Tematy**|(Brak)|Przypadek użycia|Podsystem lub innego typu, który jest właścicielem przypadek użycia.<br /><br /> Jest on ustawiany przez umieszczenie przypadek użycia w podsystemie na diagramie.|  
|**Widoczność**|Public|Użyj podsystemu przypadkach aktora,|**Publiczne** — jest to widoczne globalnie.<br /><br /> **Pakiet** — jest to widoczne w pakiecie.|  
|**IsAbstract**|False|Użyj podsystemu przypadkach aktora,|W przypadku opcji true nie można utworzyć wystąpienia typu, a ma służyć jako podstawa specjalizacji przez inne definicje.|  
|**Czy wystąpienie utworzono pośrednio**|True|Podsystem|Podsystem istnieje tylko jako artefaktów projektu. W czasie wykonywania istnieje tylko jego części.|  
|**Hiperłącze**|(Brak)|Artefakt|Ścieżka adresu URL lub pliku diagramu lub dokument, do którego artefaktu z linkiem.|  
  
 Aby uzyskać listę właściwości skojarzeń, zobacz [właściwości skojarzeń w UML, diagramy klas](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)



