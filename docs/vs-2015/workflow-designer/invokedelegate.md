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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659002"
---
# <a name="invokedelegate"></a>InvokeDelegate

Projektant **InvokeDelegate** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeDelegate> działania.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate>Wywołuje delegata publicznego.

### <a name="using-the-invokedelegate-activity-designer"></a>Korzystanie z projektanta działań InvokeDelegate

Projektanta działań **InvokeDelegate** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać pozycję **pasek narzędzi** z menu **Widok** lub Crtl + Alt + X).

Projektanta działań **InvokeDelegate** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, gdzie kiedykolwiek są zwykle umieszczane działania, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.InvokeDelegate> działania z wartością domyślną <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **InvokeDelegate** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeDelegate> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.InvokeDelegate> działania. Wartość domyślna to InvokeDelegate.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Prawda|Nazwa, <xref:System.Activities.ActivityDelegate> która ma być wywoływana, gdy działanie jest wykonywane. Tę właściwość można edytować na powierzchni projektanta. Jest to właściwość obowiązkowa.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Fałsz|Kolekcja argumentów wywołanego delegata. Klucze są nazwami <xref:System.Activities.DelegateArgument> obiektów w <xref:System.Activities.ActivityDelegate> i wartości są argumentami, których wyrażenia są oceniane i przypisywane do odpowiednich <xref:System.Activities.DelegateArgument> obiektów. W siatce właściwości kliknij przycisk wielokropka w polu **DelegateArguments** , aby umożliwić ustawienie tej właściwości. **DelegateArguments** Kliknij pole **Utwórz argument** , aby dodać argumenty.|

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)