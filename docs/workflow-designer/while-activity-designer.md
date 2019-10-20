---
title: Projektant przepływu pracy — while — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6570a80de5be17b2893fc4105f057e655e841881
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649767"
---
# <a name="while-activity-designer"></a>While, projektant działań

Działanie <xref:System.Activities.Statements.While> wykonuje działanie zawarte w jego <xref:System.Activities.Statements.While.Body%2A>, podczas gdy określony <xref:System.Activities.Statements.While.Condition%2A> ma **wartość true**. Zawarte działanie może nigdy nie zostać wykonane. Jeśli chcesz, aby zawarte działanie było wykonywane co najmniej raz, Użyj działania <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Właściwości w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne właściwości działania <xref:System.Activities.Statements.While> i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.While> projektanta działań w nagłówku. Wartość domyślna to while. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Zawiera działanie do wykonania, gdy <xref:System.Activities.Statements.While.Condition%2A> ma **wartość true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Oznacza|Zawiera wyrażenie Visual Basic, które jest oceniane, aby określić, czy działanie w <xref:System.Activities.Statements.While.Body%2A> ma zostać wykonane.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)