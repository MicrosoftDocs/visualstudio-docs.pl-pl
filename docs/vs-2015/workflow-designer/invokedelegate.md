---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659002"
---
# <a name="invokedelegate"></a>InvokeDelegate

Projektant **InvokeDelegate** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

@No__t_0 wywołuje delegata publicznego.

### <a name="using-the-invokedelegate-activity-designer"></a>Korzystanie z projektanta działań InvokeDelegate

Projektanta działań **InvokeDelegate** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CRTL + ALT + X.)

Projektanta działań **InvokeDelegate** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)]ą powierzchnię, w której są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.InvokeDelegate> przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. @No__t_0 można edytować w nagłówku projektanta działań **InvokeDelegate** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.InvokeDelegate> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.InvokeDelegate>. Wartość domyślna to InvokeDelegate.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Oznacza|Nazwa <xref:System.Activities.ActivityDelegate>, która ma być wywoływana, gdy działanie jest wykonywane. Tę właściwość można edytować na powierzchni projektanta. Jest to właściwość obowiązkowa.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekcja argumentów wywołanego delegata. Klucze są nazwami obiektów <xref:System.Activities.DelegateArgument> na <xref:System.Activities.ActivityDelegate>, a wartości to argumenty, których wyrażenia są oceniane i przypisywane do odpowiednich obiektów <xref:System.Activities.DelegateArgument>. W siatce właściwości kliknij przycisk wielokropka w polu **DelegateArguments** , aby umożliwić ustawienie tej właściwości. Kliknij pole **Utwórz argument** , aby dodać argumenty.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)