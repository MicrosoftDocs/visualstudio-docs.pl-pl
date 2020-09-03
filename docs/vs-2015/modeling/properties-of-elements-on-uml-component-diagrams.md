---
title: Właściwości elementów na diagramach składników UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671449"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Właściwości elementów na diagramach składników UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W diagramie składnika UML każdy element na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratorze modelu UML** , a następnie kliknij polecenie **Właściwości**. Właściwości są wyświetlane w oknie **Właściwości** .

> [!NOTE]
> Ten temat zawiera informacje o właściwościach elementów w diagramach składników UML. Aby uzyskać więcej informacji na temat odczytywania diagramów składników UML, zobacz [diagramy składników UML: Reference](../modeling/uml-component-diagrams-reference.md). Aby uzyskać więcej informacji na temat rysowania diagramów składników UML, zobacz [diagramy składników UML: wytyczne](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Właściwości elementów

|Właściwość|Domyślne|Element|Opis|
|--------------|-------------|-------------|-----------------|
|**Nazwa**|Nazwa domyślna|Wszystko|Identyfikuje element.|
|**Kwalifikowana nazwa**|Przestrzeń nazw:: Name|Wszystko|Jednoznacznie identyfikuje element.<br /><br /> Nazwa składnika lub typu jest poprzedzona kwalifikowaną nazwą pakietu, który go zawiera.<br /><br /> Nazwa części lub portu jest poprzedzona kwalifikowaną nazwą składnika będącego jego właścicielem.|
|**Elementy robocze**|0 skojarzone|Wszystko|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Opis**|(brak)|Wszystko|Tutaj możesz tworzyć ogólne uwagi dotyczące elementu.|
|**Kolor**|(wartość domyślna dla typu)|Składnik, część, delegowanie, zestaw części|Kolor kształtu. W przeciwieństwie do innych właściwości, jest to kolor kształtu, a nie elementu modelu wyświetlanego przez kształt.|
|**Jest pośrednio skonkretyzowany**|Prawda|Składnik|Składnik istnieje tylko jako artefakt projektowy. W czasie wykonywania tylko jego części istnieją.|
|**Jest abstrakcyjny**|Fałsz|Składnik|Definicja składnika może być używana tylko jako Generalizacja, z której mogą być wyspecjalizowane inne składniki.|
|**Widoczność**|Publiczne|Składnik, część, port|**Publiczny** — widoczny globalnie.<br /><br /> **Pakiet** widoczny w pakiecie.<br /><br /> **Prywatny** — widoczny w składniku będącym właścicielem.<br /><br /> Widoczność **chroniona** jako składniki pochodzące od właściciela.|
|**Typ**|Typ podczas tworzenia|Część<br /><br /> Port|Typ części jest składnikiem lub klasą.<br /><br /> Typ portu jest interfejsem.|
|**Kardynalność**|1|Część<br /><br /> Port|Wskazuje, ile wystąpień określonego typu jest częścią składnika nadrzędnego.<br /><br /> `1` — dokładnie jeden.<br /><br /> `0..1` -jeden lub brak.<br /><br /> `*` -Kolekcja dowolnej liczby.<br /><br /> `n..m` -Kolekcja od n do m wystąpień.|
|**Jest zachowaniem**|Fałsz|Port|W przypadku wartości true komunikaty wysyłane do tego portu są obsługiwane przez działania lub operacje, które są opisane jako część składnika, a nie jego części.|
|**Jest usługą**|Fałsz|Port|Jeśli wartość jest równa true, ten port jest częścią opublikowanego interfejsu tego składnika.|
|**LinkedPackage**|Model|Diagram|Domyślna przestrzeń nazw dla elementów dodanych do tego diagramu.|

## <a name="see-also"></a>Zobacz też
 [Diagramy przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)
