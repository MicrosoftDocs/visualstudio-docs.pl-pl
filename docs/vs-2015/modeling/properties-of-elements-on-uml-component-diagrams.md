---
title: Właściwości elementów na diagramach składników UML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb99ea1efb070c3e79b294bd5d06eedf131623f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790087"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Właściwości elementów na diagramach składników UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie składników UML każdego elementu na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratora modelu UML** a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  
  
> [!NOTE]
>  Ten temat dotyczy właściwości elementów w diagramach składników UML. Aby uzyskać więcej informacji o tym, jak odczytać diagramy składników UML, zobacz [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md). Aby uzyskać więcej informacji na temat narysować diagramy składników UML, zobacz [diagramy składników UML: wskazówki dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Właściwości elementów  
  
|Właściwość|Domyślny|Element|Opis|  
|--------------|-------------|-------------|-----------------|  
|**Nazwa**|Domyślna nazwa|Wszystkie|Identyfikuje element.|  
|**Kwalifikowana nazwa**|Namespace:: nazwy|Wszystkie|Jednoznacznie identyfikuje element.<br /><br /> Składnik lub nazwa typu jest poprzedzony znakiem kwalifikowaną nazwę pakietu, który go zawiera.<br /><br /> Część lub nazwy portu jest poprzedzony znakiem kwalifikowana nazwa składnika, który jest jego właścicielem.|  
|**Elementy robocze**|skojarzone 0|Wszystkie|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Opis**|(Brak)|Wszystkie|Można wprowadzić ogólne uwagi na temat elementu, w tym miejscu.|  
|**Kolor**|(wartość domyślna dla typu)|Część, delegowanie, zestaw części składnika|Kolor kształtu. W przeciwieństwie do innych właściwości jest to kolor kształtu, a nie do elementu modelu, który wyświetla kształtu.|  
|**Czy wystąpienie utworzono pośrednio**|True|Składnik|Składnik istnieje tylko jako artefaktów projektu. W czasie wykonywania istnieje tylko jego części.|  
|**Jest abstrakcyjna**|False|Składnik|Definicja składnika może służyć jedynie jako Generalizacja, z której można wyspecjalizować innych składników.|  
|**Widoczność**|Public|Składnik, części, Port|**Publiczne** — jest to widoczne globalnie.<br /><br /> **Pakiet** — jest to widoczne w pakiecie.<br /><br /> **Prywatne** — jest to widoczne w składniku będącej właścicielem.<br /><br /> **Chronione** — widoczny dla składników pochodzące od właściciela.|  
|**Typ**|Wpisz przy tworzeniu|Część<br /><br /> Port|Typ części jest składnika lub klasy.<br /><br /> Typ portu jest interfejsem.|  
|**Liczebność**|1|Część<br /><br /> Port|Wskazuje, ile wystąpień określonego typu stanowią część składnika nadrzędnego.<br /><br /> `1` — dokładnie jeden.<br /><br /> `0..1` -jednego lub Brak.<br /><br /> `*` -kolekcję dowolnej liczby.<br /><br /> `n..m` — zbierania od n do m wystąpień.|  
|**To zachowanie**|False|Port|W przypadku opcji true, wiadomości do tego portu są obsługiwane przez działania lub operacje, które są opisane w ramach składnika, a nie jej części.|  
|**Usługa**|False|Port|W przypadku opcji true ten port jest częścią opublikowanego interfejsu tego składnika.|  
|**LinkedPackage**|Model|Diagram|Domyślny obszar nazw dla elementów dodanych do tego diagramu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)



