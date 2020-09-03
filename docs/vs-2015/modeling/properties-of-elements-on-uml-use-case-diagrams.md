---
title: Właściwości elementów na diagramach przypadków użycia UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671415"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Właściwości elementów na diagramach przypadków użycia UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie przypadku użycia UML każdy element na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratorze modelu UML** , a następnie kliknij polecenie **Właściwości**. Właściwości są wyświetlane w oknie **Właściwości** .

> [!NOTE]
> Ten temat zawiera informacje o właściwościach elementów w diagramach przypadków użycia UML. Aby uzyskać więcej informacji na temat odczytywania diagramów aktywności UML, zobacz [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md). Aby uzyskać więcej informacji na temat rysowania diagramów aktywności UML, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Właściwości elementów

|Właściwość|Domyślne|Element|Opis|
|--------------|-------------|-------------|-----------------|
|**Nazwa**|Nazwa domyślna|Wszystko|Identyfikuje element.|
|**Kwalifikowana nazwa**|Pakiet:: Nazwa|Wszystko|Jednoznacznie identyfikuje element. Poprzedzona nazwą kwalifikowaną pakietu, która go zawiera.|
|**Elementy robocze**|0 skojarzone|Wszystko|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Opis**|(brak)|Wszystko|Tutaj możesz tworzyć ogólne uwagi dotyczące elementu.|
|**Kolor**|(wartość domyślna)|Wszystko|Kolor kształtu. W przeciwieństwie do innych właściwości, nie jest to właściwość elementu wyświetlanego przez kształt.|
|**Ścieżka obrazu**|(brak)|Aktor|Ścieżka do pliku obrazu, który ma zostać użyty zamiast domyślnej ikony aktora. Ikona powinna być plikiem zasobów w projekcie programu Visual Studio.|
|**Tematy**|(brak)|Przypadek użycia|Podsystem lub inny typ, który jest właścicielem przypadku użycia.<br /><br /> Można ją ustawić, umieszczając przypadek użycia w podsystemie na diagramie.|
|**Widoczność**|Publiczne|Przypadek użycia, aktor, podsystem|**Publiczny** — widoczny globalnie.<br /><br /> **Pakiet** widoczny w pakiecie.|
|**IsAbstract**|Fałsz|Przypadek użycia, aktor, podsystem|Jeśli wartość jest równa true, typ nie może być skonkretyzowany i jest przeznaczony jako podstawa dla specjalizacji przez inne definicje.|
|**Jest pośrednio skonkretyzowany**|Prawda|Wykonawc|Podsystem istnieje tylko jako artefakt projektowy. W czasie wykonywania tylko jego części istnieją.|
|**Hyperlink**|(brak)|Artefakt|Adres URL lub ścieżka pliku diagramu lub dokumentu, do którego artefakt zawiera link.|

 Aby uzyskać listę właściwości skojarzeń, zobacz [Właściwości skojarzeń na diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Zobacz też
 [Diagramy przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)
