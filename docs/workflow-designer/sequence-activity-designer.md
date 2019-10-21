---
title: Projektant przepływu pracy — Projektant działań w sekwencji
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 116e8c31a6d7cad2e5c6da95bc66e34a0d11163a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649947"
---
# <a name="sequence-activity-designer"></a>Sequence, projektant działań

Działanie <xref:System.Activities.Statements.Sequence> zawiera uporządkowaną kolekcję działań podrzędnych wykonywanych w określonej kolejności.

Innym sposobem wykonania zestawu działań jest użycie działania <xref:System.Activities.Statements.Flowchart>. Należy rozważyć użycie [schematu blokowego](../workflow-designer/flowchart-activity-designer.md) , gdy istnieje prosty przepływ programu rozgałęziania lub zapętlenia, który ma być modelem diagrammatically.

## <a name="using-the-sequence-activity-designer"></a>Korzystanie z projektanta działania sekwencji

Aby dodać działanie <xref:System.Activities.Statements.Sequence>, przeciągnij projektanta działania **sekwencji** z **przybornika** i upuść go na powierzchni Projektant przepływu pracy. Aby dodać działanie podrzędne do tego działania <xref:System.Activities.Statements.Sequence>, przeciągnij inne działanie z **przybornika** i upuść je na Trójkącie w polu zawierającym tekst wskazówki "upuść działanie tutaj".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Właściwości działania sekwencji w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Sequence> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Sequence> projektanta działań w nagłówku. Wartość domyślna to Sequence. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)