---
title: PickBranch — Projektant działań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672583"
---
# <a name="pickbranch-activity-designer"></a>PickBranch, projektant działań
<xref:System.Activities.Statements.PickBranch>Zapewnia ścieżkę wykonywania w ramach <xref:System.Activities.Statements.Pick> działania, które może zostać wyzwolone przez zdarzenie przychodzące.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> obiekty są zawarte w <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji <xref:System.Activities.Statements.Pick> działań. Każda z nich <xref:System.Activities.Statements.PickBranch> jest zawarta w gałęzi <xref:System.Activities.Statements.Pick> działania i może być wykonana z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób [!INCLUDE[wfd1](../includes/wfd1-md.md)] zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> a i <xref:System.Activities.Statements.PickBranch.Action%2A> .

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru
 Projektanta **PickBranch** można znaleźć w kategorii **przepływ sterowania** w **przyborniku**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X).

 Dwa puste <xref:System.Activities.Statements.PickBranch> obiekty z nazwami wyświetlanymi **Branch1** i **Branch2** są tworzone domyślnie jako elementy <xref:System.Activities.Statements.Pick> działania po początkowym **pobraniu** projektanta działań na [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Te odpowiednie <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości można edytować w nagłówku projektanta **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

 Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiektów do kolekcji <xref:System.Activities.Statements.Pick> obiektów: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu kontekstowego z poziomu powierzchni projektowej **wyboru** :

1. Projektant **PickBranch** tworzy <xref:System.Activities.Statements.PickBranch> gdy jest przeciągany z **przybornika** i upuszczany do jednej z gałęzi projektanta działań **wyboru** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni. Nowe <xref:System.Activities.Statements.PickBranch> obiekty można umieścić wewnątrz <xref:System.Activities.Statements.Pick> projektanta po lewej lub prawej stronie wszelkich istniejących elementów znajdujących się <xref:System.Activities.Statements.PickBranch> już w kolekcji. Gdy przeciągasz projektanta **PickBranch** do projektanta **wyboru** z myszą, Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> zostanie dodany dla danego położenia myszy.

2. Kliknij prawym przyciskiem myszy pozycję **Wybierz** projektanta działań (ale nie wewnątrz projektanta **PickBranch** ), aby uzyskać menu kontekstowe i wybierz polecenie **Utwórz gałąź** , aby dodać nowy element <xref:System.Activities.Statements.PickBranch> . Zwróć uwagę, że nowy <xref:System.Activities.Statements.PickBranch> zostanie dodany po prawej stronie istniejących <xref:System.Activities.Statements.PickBranch> obiektów w projektancie **wyboru** .

   Projektanta **PickBranch** można rozszerzyć, aby odsłonić pola **wyzwalacza** i **akcji** lub zwinięte przez kliknięcie podwójnego karetki po prawej stronie jego nagłówków. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> każdego z nich, <xref:System.Activities.Statements.PickBranch> usuwając działania do pól **wyzwalacz** i **Akcja** w swoich projektantach.

   <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> Można zmienić kolejność obiektów w kolekcji obiektów, przeciągając je i upuszczając do nowej lokalizacji w projektancie **wyboru** . Projektant **wyboru** używa pionowego niebieskiego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> zostanie dodany dla danego położenia myszy.

   Istnieją dwa sposoby usunięcia <xref:System.Activities.Statements.PickBranch> :

3. Wybierz projektanta **PickBranch** i usuń go.

4. Wybierz projektanta **PickBranch** , kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz pozycję **Usuń**.

   Pamiętaj, aby wybrać projektanta **PickBranch** , wybierając jedno z działań wewnątrz jego **wyzwalacza** lub **akcji** przez pomyłkę usuwa jedną z tych działań, a nie <xref:System.Activities.Statements.PickBranch> obiekt.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości i opisano sposób ich używania w programie [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Fałsz|Przyjazna nazwa wyświetlana w nagłówku projektanta **PickBranch** . Wartość domyślna to gałąź.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Prawda|Każda <xref:System.Activities.Statements.PickBranch> z nich zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> akcję, która może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A> .|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Fałsz|Każdy <xref:System.Activities.Statements.PickBranch> z nich zawiera element <xref:System.Activities.Statements.PickBranch.Action%2A> , który jest wykonywany, gdy zostanie wyzwolony.|

## <a name="see-also"></a>Zobacz też
 [Działanie pobrania](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [przepływu sterowania](../workflow-designer/control-flow-activity-designers.md) [przy użyciu działania pobrania](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)