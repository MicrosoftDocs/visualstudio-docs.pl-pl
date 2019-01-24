---
title: Składnia ścieżki domeny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c115e8fff6cddbc1b08c697b72c7bda3a970ed4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802104"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definicji DSL użyć składni XPath, aby zlokalizować określonych elementów w modelu.  
  
 Zazwyczaj nie trzeba pracować przy użyciu tej składni bezpośrednio. Położenia szczegóły języka DSL lub w oknie właściwości, można kliknąć strzałkę w dół i za pomocą edytora ścieżki. Jednak w tym formularzu w polu pojawia się ścieżkę, po zastosowaniu edytora.  
  
 Ścieżka domeny ma następującą postać:  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![CommentReferencesSubjects odwoływać się do relacji](../modeling/media/dsl-reference.png "dsl_reference")  
  
 Składnia przesyłane za pośrednictwem drzewa modelu. Na przykład relacji domeny **CommentReferencesSubjects** na ilustracji powyżej ma **przedmioty** roli. Segment ścieżki **/! Subjectt** Określa, że ścieżka kończy się na elementach dostępne za pośrednictwem **przedmioty** roli.  
  
 Każdy z segmentów rozpoczyna się od nazwy relacji domeny. W przypadku przechodzenia z elementu do relacji, segment ścieżki jest wyświetlany jako *Relationship.PropertyName*. W przypadku przeskok z linku do elementu, segment ścieżki jest wyświetlany jako *relacji /! RoleName*.  
  
 Ukośniki oddzielne składnia ścieżki. Każdy z segmentów ścieżki jest albo przeskoków, z elementu łącza (wystąpienie relacji) lub łącze do elementu. Segmenty ścieżki często są wyświetlane w pary. Jeden segment ścieżki reprezentuje przeskoku z elementu łącza i następny segment reprezentuje przeskoku przy użyciu linku na element na drugim końcu. (Dowolny link może być również źródłową lub docelową relacji, sam).  
  
 Nazwa, której używa przeskoku łącze elementu jest wartością roli `Property Name`. To nazwa używana dla elementu łącza przeskoku przez jest nazwa roli docelowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
