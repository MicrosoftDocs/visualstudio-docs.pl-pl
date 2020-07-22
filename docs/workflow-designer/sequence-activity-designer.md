---
title: Projektant przepływu pracy — Projektant działań w sekwencji
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77980077a580724f6db6bb5a544200890421d8e5
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875972"
---
# <a name="sequence-activity-designer"></a>Sequence, projektant działań

<xref:System.Activities.Statements.Sequence>Działanie zawiera uporządkowaną kolekcję działań podrzędnych wykonywanych w określonej kolejności.

Innym sposobem wykonania zestawu działań jest użycie <xref:System.Activities.Statements.Flowchart> działania. Należy rozważyć użycie [schematu blokowego](../workflow-designer/flowchart-activity-designer.md) , gdy istnieje prosty przepływ programu rozgałęziania lub zapętlenia, który ma być modelem diagrammatically.

## <a name="using-the-sequence-activity-designer"></a>Korzystanie z projektanta działania sekwencji

Aby dodać <xref:System.Activities.Statements.Sequence> działanie, przeciągnij projektanta działania **sekwencji** z **przybornika** i upuść go na powierzchnię Projektant przepływu pracy. Aby dodać działanie podrzędne do tego <xref:System.Activities.Statements.Sequence> działania, przeciągnij inne działanie z **przybornika** i upuść je na Trójkącie w polu zawierającym tekst wskazówki "upuść działanie tutaj".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Właściwości działania sekwencji w Projektant przepływu pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Sequence> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.Sequence> projektanta działań w nagłówku. Wartość domyślna to Sequence. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)