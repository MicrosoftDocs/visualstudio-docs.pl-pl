---
title: Wybierz projektanta działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672595"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań
<xref:System.Activities.Statements.Pick>Działanie zapewnia przepływ sterowania oparty na zdarzeniach. Działanie wykonuje jedną z kilku gałęzi w odpowiedzi na zdarzenie wyzwalające.

## <a name="the-pick-activity"></a>Działanie pobrania
 <xref:System.Activities.Statements.Pick>Działanie zawiera kolekcję <xref:System.Activities.Statements.PickBranch> obiektów, z których jedno <xref:System.Activities.Statements.Pick> działanie może zostać wykonane z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób [!INCLUDE[wfd1](../includes/wfd1-md.md)] zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> a i <xref:System.Activities.Statements.PickBranch.Action%2A> . Na początku <xref:System.Activities.Statements.Pick> wykonywania działania są planowane wszystkie działania wyzwalacza <xref:System.Activities.Statements.PickBranch> elementów. Po zakończeniu pierwszego działania zostanie zaplanowana odpowiednia aktywność działania, a wszystkie inne działania wyzwalacza są anulowane.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru
 Projektanta działań **wyboru** można znaleźć w kategorii **przepływ sterowania** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Można przeciągać **projektanta działań z** **przybornika** i upuszczać na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchnię, wszędzie tam, gdzie projektanci aktywności są zwykle umieszczane na przykład w ramach projektanta działania **sekwencji** . Po porzucenie go do [!INCLUDE[wfd2](../includes/wfd2-md.md)] programu tworzy <xref:System.Activities.Statements.Pick> działanie, które domyślnie zawiera dwa puste <xref:System.Activities.Statements.PickBranch> działania jako elementy z nazwami wyświetlanymi Branch1 i Branch2. Te odpowiednie <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości można edytować w nagłówku projektanta działań **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

 Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> działań do kolekcji <xref:System.Activities.Statements.Pick> obiektów: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu kontekstowego z poziomu powierzchni projektowej **wyboru** . Aby uzyskać szczegółowe informacje, zobacz temat [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Należy zauważyć, że jedynym elementem, który można umieścić wewnątrz projektanta działań **wyboru** , jest **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektant przepływu pracy
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Pick> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> projektanta działań w nagłówku. Wartość domyślna to wybierz. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|

## <a name="see-also"></a>Zobacz też
 [Działanie pobrania](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [przepływu sterowania](../workflow-designer/control-flow-activity-designers.md) [przy użyciu działania pobrania](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)