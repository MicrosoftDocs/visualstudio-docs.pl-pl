---
title: Projektant przepływu pracy — InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650178"
---
# <a name="invokedelegate"></a>InvokeDelegate

Projektant **InvokeDelegate** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

@No__t_0 wywołuje delegata publicznego.

### <a name="use-the-invokedelegate-activity-designer"></a>Korzystanie z projektanta działań InvokeDelegate

Dostęp do projektanta działań **InvokeDelegate** w kategorii elementy **pierwotne** w **przyborniku**. Projektanta działań **InvokeDelegate** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracyą powierzchnię, w której są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.Activities.Statements.InvokeDelegate> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. @No__t_0 można edytować w nagłówku projektanta działań **InvokeDelegate** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.InvokeDelegate> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.InvokeDelegate>. Wartość domyślna to InvokeDelegate.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepiej użyć jednej z nich.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Oznacza|Nazwa <xref:System.Activities.ActivityDelegate>, która ma być wywoływana, gdy działanie jest wykonywane. Tę właściwość można edytować na powierzchni projektanta i jest obowiązkowe.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekcja argumentów wywołanego delegata. Klucze są nazwami obiektów parametrów w <xref:System.Activities.ActivityDelegate>, a wartości to argumenty, których wyrażenia są oceniane i przypisywane do odpowiednich obiektów parametrów. Aby wyświetlić okno dialogowe **DelegateArguments** , w którym można ustawić tę właściwość, kliknij przycisk wielokropka w polu **DelegateArguments** siatki właściwości. Kliknij pole **Utwórz argument** , aby dodać argumenty.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)