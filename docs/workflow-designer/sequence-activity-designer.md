---
title: Projektant przepływu pracy — Sequence, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abbffa44ee7fa4db2a03e5f46820f707cae8d4fb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928377"
---
# <a name="sequence-activity-designer"></a>Sequence, projektant działań

<xref:System.Activities.Statements.Sequence> Zawiera działanie uporządkowany zbiór działania podrzędne, które wykonuje się w kolejności.

Innym sposobem wykonywania zestawu działań w kolejności jest użycie <xref:System.Activities.Statements.Flowchart> działania. Należy rozważyć użycie [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) przypadku rozgałęzianie proste lub pętli przepływu programu, który ma być schematycznie modelu.

## <a name="using-the-sequence-activity-designer"></a>Za pomocą Sequence, Projektant działań

Aby dodać <xref:System.Activities.Statements.Sequence> działania, przeciągnij **sekwencji** projektanta działań z **przybornika** i upuść je na powierzchni projektanta przepływów pracy. Aby dodać działanie podrzędne do tego <xref:System.Activities.Statements.Sequence> działania, przeciągnij jakieś działania, od **przybornika** i upuść je na trójkąt w polu z tekst wskazówki "Upuść działanie tutaj".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Właściwości działania sekwencji w Projektancie przepływu pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Sequence> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Sequence> projektanta działań w nagłówku. Wartość domyślna to sekwencji. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)