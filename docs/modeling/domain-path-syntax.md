---
title: Składnia ścieżki domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37255345c1d394130872dc65a8568309a3091347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747575"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicje DSL używają składni podobnej do XPath do lokalizowania określonych elementów w modelu.

 Zwykle nie trzeba bezpośrednio korzystać z tej składni. Gdzie pojawia się w szczegółach lub okno Właściwościach DSL, możesz kliknąć strzałkę w dół i użyć edytora ścieżek. Ścieżka jest jednak wyświetlana w tym formularzu w polu po użyciu edytora.

 Ścieżka domeny ma następującą postać:

 *RelationshipName. PropertyName/! Roli*

 ![Relacja odwołania CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 Składnia przechodzi przez drzewo modelu. Na przykład Relacja domeny **CommentReferencesSubjects** na powyższej ilustracji ma rolę **podmiot** . Segment ścieżki **/! Wartość określa,** że ścieżka kończy się na elementach, do których można uzyskać dostęp za pomocą roli **podmiot** .

 Każdy segment zaczyna się od nazwy relacji domeny. Jeśli przechodzenie pochodzi z elementu do relacji, segment ścieżki zostanie wyświetlony jako *Relationship. PropertyName*. Jeśli przeskok pochodzi z linku do elementu, segment ścieżki jest wyświetlany jako *relacja/! Rolename*.

 Ukośniki oddzielają składnię ścieżki. Każdy segment ścieżki jest przeskokiem z elementu do linku (wystąpienie relacji) lub z linku do elementu. Segmenty ścieżki często pojawiają się w parach. Jeden segment ścieżki reprezentuje przeskok z elementu do linku, a następny segment reprezentuje przeskok z linku do elementu na drugim końcu. (Dowolne łącze może być również źródłem lub obiektem docelowym relacji).

 Nazwa, która jest używana na potrzeby przeskoku elementu do linku, jest wartością `Property Name` roli. Nazwa użyta dla przeskoku link-element jest nazwą roli docelowej.

## <a name="see-also"></a>Zobacz także

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)