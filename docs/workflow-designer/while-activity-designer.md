---
title: Projektant przepływu pracy — podczas Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d9ea1f6bd42526eb0ea38c23cbf0f28c4346515
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953249"
---
# <a name="while-activity-designer"></a>While, projektant działań

<xref:System.Activities.Statements.While> Działanie wykonuje działania zawarte w jego <xref:System.Activities.Statements.While.Body%2A> podczas określonego <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**. Zawarte działanie nigdy nie może zostać wykonany. Jeśli chcesz, aby zawarte działanie do wykonania, co najmniej raz, użyj <xref:System.Activities.Statements.DoWhile> działania zamiast tego.

## <a name="while-properties-in-workflow-designer"></a>Podczas gdy właściwości w Projektancie przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.While> właściwości działania i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.While> projektanta działań w nagłówku. Wartość domyślna to a. Wartość może być edytowana w **właściwości** okna lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Zawiera działanie do wykonania podczas <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Prawda|Zawiera wyrażenie języka Visual Basic, które jest obliczane, aby określić, czy działania w <xref:System.Activities.Statements.While.Body%2A> ma zostać wykonana.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)