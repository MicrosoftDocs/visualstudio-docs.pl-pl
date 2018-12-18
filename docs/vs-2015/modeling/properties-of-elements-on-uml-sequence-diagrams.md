---
title: Właściwości elementów na UML, diagramy sekwencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 01d63e39967df361d87ff0182b1c85b6ecd2fdb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793901"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Właściwości elementów w diagramach sekwencji UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie sekwencji UML każdego elementu na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratora modelu UML** a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  
  
> [!NOTE]
>  Ten temat dotyczy właściwości elementów w diagramach sekwencji UML. Aby uzyskać więcej informacji o tym, jak odczytać diagramy sekwencji UML, zobacz [diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md). Aby uzyskać więcej informacji na temat narysować diagramy sekwencji UML, zobacz [UML Sequence Diagrams: wskazówki dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Właściwości elementów  
  
|Właściwość|Domyślny|Element|Opis|  
|--------------|-------------|-------------|-----------------|  
|**Nazwa**|Domyślna nazwa|Wszystkie|Identyfikuje element.|  
|**Kwalifikowana nazwa**|Pakiet:: nazwy|Wszystkie|Jednoznacznie identyfikuje element. Prefiks kwalifikowaną nazwę pakietu, który go zawiera.|  
|**Elementy robocze**|skojarzone 0|Wszystkie|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Opis**|(pusty)|Wszystkie|Można wprowadzić ogólne uwagi dotyczące elementu w tym miejscu.|  
|**Kolor**|(wartość domyślna dla typu elementu)|Linia życia, wiadomości|Kolor kształtu. Jest to właściwość kształtu, zamiast element Wyświetla.|  
|**Typ**|(pusty)|Linia życia|Typ wystąpienia, która reprezentuje linii życia.<br /><br /> W przypadku symbolu odwołania wyświetlane w nagłówku linii życia, następnie tej klasy lub interfejsu w Eksploratorze modelu UML istnieje oddzielnie i mogą być wyświetlane na diagramie klasy.|  
|**aktora**|False|Linia życia|Wskazuje, czy linia życia reprezentuje użytkownika, urządzenia lub oprogramowania składnik, który znajduje się poza składnik, który dotyczy diagramu.|  
|**rodzaj**|**Pełne** — wiadomość, która ma zarówno nadawcy i odbiorcy.<br /><br /> **Znaleziono** -komunikat, który ma nieokreślony nadawcę.<br /><br /> **Utracono** -komunikat, który ma nieokreślony odbiorcy.|Komunikat|Wskazuje, której kończy się wiadomości są dołączone do linii życia.<br /><br /> Nie można zmienić tej właściwości. Podczas tworzenia komunikatu jest ustawiona.|  
|**Sortowanie**|**AsynchCall** -komunikatów asynchronicznych.<br /><br /> **SynchCall** -synchronicznego komunikatu.<br /><br /> **Odpowiedź** -return części synchronicznego komunikatu.<br /><br /> **CreateMessage** -komunikat utworzenia wystąpienia.|Komunikat|Typ komunikatu. Nie można zmienić tej właściwości. Zostanie ono określone przez to narzędzie umożliwia tworzenie komunikatu.|  
|**Operacja**|(pusty)|Komunikat|Metoda wywoływana przez wiadomość na odbieranie linii życia.<br /><br /> Widoczne tylko wtedy, gdy odbieranie linii życia jest połączony interfejs lub klasę.|  
|**Odwołuje się do**|Diagram sekwencji|Wykorzystanie interakcji|Diagram sekwencji, wywoływana przy użyciu tej interakcji.|  
|**Operator interakcji**|Ustawiana, jeśli użyto **Otocz** polecenia|Połączony Fragment|Operator, reprezentowane przez ten fragment lub zbiór fragmentów.|  
|**Ochrona**|(pusty)|Operand interakcji w połączony Fragment|Kolejność w fragment zostanie przeprowadzona, chyba że osłony ma wartość true.<br /><br /> Aby wybrać najważniejsze fragmentu wszelkie połączonego fragmentu, kliknij pod tytułem fragmentu.|  
|**Wartość minimalna, maksymalna liczba**|(nie ograniczenia)|Pętla połączony Fragment|Minimalna i maksymalna liczba przypadków, gdy jest wykonywana pętla.|  
|**Komunikaty**|(pusty)|Należy wziąć pod uwagę i<br /><br /> Ignoruj połączonego fragmentu|Komunikaty, które są uważane za lub ignorowane w tym fragmencie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



