---
title: Składnia ścieżki domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 13a8ab293a6a18856ba98edc7aa04154bc876d40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834935"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicji DSL użyć składni XPath, aby zlokalizować określonych elementów w modelu.

 Zazwyczaj nie trzeba pracować przy użyciu tej składni bezpośrednio. Położenia szczegóły języka DSL lub w oknie właściwości, można kliknąć strzałkę w dół i za pomocą edytora ścieżki. Jednak w tym formularzu w polu pojawia się ścieżkę, po zastosowaniu edytora.

 Ścieżka domeny ma następującą postać:

 *RelationshipName.PropertyName/!Role*

 ![Odwołania obiektu CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 Składnia przesyłane za pośrednictwem drzewa modelu. Na przykład relacji domeny **CommentReferencesSubjects** na ilustracji powyżej ma **przedmioty** roli. Segment ścieżki **/! Subjectt** Określa, że ścieżka kończy się na elementach dostępne za pośrednictwem **przedmioty** roli.

 Każdy z segmentów rozpoczyna się od nazwy relacji domeny. W przypadku przechodzenia z elementu do relacji, segment ścieżki jest wyświetlany jako *Relationship.PropertyName*. W przypadku przeskok z linku do elementu, segment ścieżki jest wyświetlany jako *relacji /! RoleName*.

 Ukośniki oddzielne składnia ścieżki. Każdy z segmentów ścieżki jest albo przeskoków, z elementu łącza (wystąpienie relacji) lub łącze do elementu. Segmenty ścieżki często są wyświetlane w pary. Jeden segment ścieżki reprezentuje przeskoku z elementu łącza i następny segment reprezentuje przeskoku przy użyciu linku na element na drugim końcu. (Dowolny link może być również źródłową lub docelową relacji, sam).

 Nazwa, której używa przeskoku łącze elementu jest wartością roli `Property Name`. To nazwa używana dla elementu łącza przeskoku przez jest nazwa roli docelowej.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)