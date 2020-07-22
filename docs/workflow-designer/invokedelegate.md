---
title: Projektant przepływu pracy — InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876076"
---
# <a name="invokedelegate"></a>InvokeDelegate

Projektant **InvokeDelegate** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeDelegate> działania.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate>Wywołuje delegata publicznego.

### <a name="use-the-invokedelegate-activity-designer"></a>Korzystanie z projektanta działań InvokeDelegate

Dostęp do projektanta działań **InvokeDelegate** w kategorii elementy **pierwotne** w **przyborniku**. Projektanta działań **InvokeDelegate** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, gdzie kiedykolwiek są zwykle umieszczane działania, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Porzucenie projektanta działań powoduje utworzenie <xref:System.Activities.Statements.InvokeDelegate> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **InvokeDelegate** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeDelegate> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.InvokeDelegate> działania. Wartość domyślna to InvokeDelegate.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepiej użyć jednej z nich.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Prawda|Nazwa, <xref:System.Activities.ActivityDelegate> która ma być wywoływana, gdy działanie jest wykonywane. Tę właściwość można edytować na powierzchni projektanta i jest obowiązkowe.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Fałsz|Kolekcja argumentów wywołanego delegata. Klucze są nazwami obiektów parametrów w <xref:System.Activities.ActivityDelegate> , a wartości są argumentami, których wyrażenia są oceniane i przypisywane do odpowiednich obiektów parametrów. Aby wyświetlić okno dialogowe **DelegateArguments** , w którym można ustawić tę właściwość, kliknij przycisk wielokropka w polu **DelegateArguments** siatki właściwości. Kliknij pole **Utwórz argument** , aby dodać argumenty.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)