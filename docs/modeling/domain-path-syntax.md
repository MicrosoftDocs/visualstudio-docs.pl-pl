---
title: Składnia ścieżki domeny
description: Dowiedz się więcej na temat składni ścieżki domeny i sposobu, w jaki definicje DSL używają składni podobnej do XPath do lokalizowania określonych elementów w modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69dfd02dca5ead65d4f36303e547aaeba04cde98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389101"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicje DSL używają składni podobnej do XPath do lokalizowania określonych elementów w modelu.

 Zazwyczaj nie trzeba pracować bezpośrednio z tą składnią. Tam, gdzie pojawia się on w obszarze szczegółów DSL lub okno Właściwości, możesz kliknąć strzałkę w dół i użyć edytora ścieżek. Jednak ścieżka zostanie wyświetlona w tym formularzu w polu po zakończeniu pracy z edytorem.

 Ścieżka domeny ma następującą postać:

 *RelationshipName.PropertyName/! Roli*

 ![CommentReferencesSubjects reference relationship (Relacja odwołania CommentReferencesSubjects)](../modeling/media/dsl_reference.png)

 Składnia przechodzi przez drzewo modelu. Na przykład relacja domeny **CommentReferencesSubjects** na powyższej ilustracji ma rolę **Podmioty.** Segment ścieżki **/! Subjectt** określa, że ścieżka kończy się na elementach dostępnych za pośrednictwem **roli Podmioty.**

 Każdy segment rozpoczyna się od nazwy relacji domeny. Jeśli przechodzenie pochodzi z elementu do relacji, segment ścieżki jest wyświetlany jako *Relationship.PropertyName*. Jeśli przeskok pochodzi z linku do elementu, segment ścieżki jest wyświetlany jako *Relacja/! Nazwa roli*.

 Ukośniki oddzielają składnię ścieżki. Każdy segment ścieżki to przeskok z elementu do linku (wystąpienie relacji) lub z linku do elementu. Segmenty ścieżki często są wyświetlane w parach. Jeden segment ścieżki reprezentuje przeskok z elementu do łącza, a następny segment reprezentuje przeskok z łącza do elementu na drugim końcu. (Dowolny link może być również źródłem lub obiektem docelowym samej relacji).

 Nazwa, która jest używana dla przeskoku element-link jest wartością roli `Property Name` . Nazwa, która jest używana dla przeskoku link do elementu jest nazwą roli docelowej.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
