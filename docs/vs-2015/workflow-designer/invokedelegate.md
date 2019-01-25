---
title: InvokeDelegate | Dokumentacja firmy Microsoft
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798912"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** projektanta jest używany do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeDelegate> działania.

## <a name="the-invokedelegate-activity"></a>Działanie InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> Wywołuje Delegat publiczny.

### <a name="using-the-invokedelegate-activity-designer"></a>Za pomocą InvokeDelegate Projektant działań

**InvokeDelegate** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** kartę [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)

**InvokeDelegate** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni gdziekolwiek działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.InvokeDelegate> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **InvokeDelegate** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokedelegate-properties"></a>Właściwości InvokeDelegate

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeDelegate> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)]powierzchni projektowej.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeDelegate> działania. Wartość domyślna to InvokeDelegate.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Prawda|Nazwa <xref:System.Activities.ActivityDelegate> wywoływana, gdy działanie wykonuje. Tej właściwości można edytować na powierzchni projektowej. To jest obowiązkowa.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Kolekcja argument wywoływany delegat. Klucze są nazwami <xref:System.Activities.DelegateArgument> obiektów na <xref:System.Activities.ActivityDelegate> i wartości argumentów, których wyrażenia są obliczane i przypisane do odpowiednich <xref:System.Activities.DelegateArgument> obiektów. W siatce właściwości kliknij przycisk z wielokropkiem w **DelegateArguments** pola, wyświetla **DelegateArguments** okno dialogowe pozwala ustawić tę właściwość. Kliknij przycisk **Utwórz Argument** pola w celu dodania argumenty.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)