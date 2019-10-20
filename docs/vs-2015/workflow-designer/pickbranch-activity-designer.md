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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672583"
---
# <a name="pickbranch-activity-designer"></a>PickBranch, projektant działań
@No__t_0 zapewnia ścieżkę wykonywania wykonywaną na podstawie zdarzeń w ramach działania <xref:System.Activities.Statements.Pick>, które mogą być wyzwalane przez zdarzenie przychodzące.

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> obiekty są zawarte w kolekcji <xref:System.Activities.Statements.Pick.Branches%2A> działania <xref:System.Activities.Statements.Pick>. Każda <xref:System.Activities.Statements.PickBranch> jest zawarta w gałęzi działania <xref:System.Activities.Statements.Pick> i może być wykonywana z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób [!INCLUDE[wfd1](../includes/wfd1-md.md)] zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każda <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru
 Projektanta **PickBranch** można znaleźć w kategorii **przepływ sterowania** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** w [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub Ctrl + Alt + X).

 Dwa puste obiekty <xref:System.Activities.Statements.PickBranch> z nazwami wyświetlanymi **Branch1** i **Branch2** są tworzone domyślnie jako elementy działania <xref:System.Activities.Statements.Pick>, gdy Projektant działań **wybierze** początkowo został porzucony w [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Te odpowiednie wartości właściwości <xref:System.Activities.Statements.PickBranch.DisplayName%2A> można edytować w nagłówku projektanta **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

 Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiektów do kolekcji obiektu <xref:System.Activities.Statements.Pick>: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika** lub za pomocą menu kontekstowego z poziomu powierzchni projektowej **wyboru** :

1. Projektant **PickBranch** tworzy <xref:System.Activities.Statements.PickBranch>, gdy jest przeciągany z **przybornika** i upuszczany do jednej z gałęzi projektanta działań **wyboru** na powierzchni [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Nowe obiekty <xref:System.Activities.Statements.PickBranch> mogą być umieszczane wewnątrz projektanta <xref:System.Activities.Statements.Pick> po lewej lub po prawej stronie wszelkich istniejących elementów <xref:System.Activities.Statements.PickBranch> już zawartych w kolekcji. Gdy przeciągasz projektanta **PickBranch** na projektanta **wyboru** z myszą, Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawane dla danego położenia myszy.

2. Kliknij prawym przyciskiem myszy pozycję **Wybierz** projektanta działań (ale nie wewnątrz projektanta **PickBranch** ), aby uzyskać menu kontekstowe, a następnie wybierz pozycję **Utwórz gałąź** , aby dodać nowe <xref:System.Activities.Statements.PickBranch>. Zwróć uwagę, że nowe <xref:System.Activities.Statements.PickBranch> są dodawane z prawej strony istniejących <xref:System.Activities.Statements.PickBranch> obiektów w projektancie **wyboru** .

   Projektanta **PickBranch** można rozszerzyć, aby odsłonić pola **wyzwalacza** i **akcji** lub zwinięte przez kliknięcie podwójnego karetki po prawej stronie jego nagłówków. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> poszczególnych <xref:System.Activities.Statements.PickBranch> przez usunięcie działań do pól **wyzwalacz** i **Akcja** w swoich projektantach.

   @No__t_0 obiektów w kolekcji <xref:System.Activities.Statements.Pick.Branches%2A> obiektu <xref:System.Activities.Statements.Pick>, można zmienić kolejność przez przeciąganie i upuszczanie ich do nowej lokalizacji w projektancie **wyboru** . Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawany dla danego położenia myszy.

   Istnieją dwa sposoby usunięcia <xref:System.Activities.Statements.PickBranch>:

3. Wybierz projektanta **PickBranch** i usuń go.

4. Wybierz projektanta **PickBranch** , kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz pozycję **Usuń**.

   Pamiętaj, aby wybrać projektanta **PickBranch** , wybierając jedno z działań wewnątrz jego **wyzwalacza** lub **akcji** przez pomyłkę powoduje usunięcie jednej z tych działań, a nie obiektu <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektant przepływu pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości i opisano sposób ich używania w [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Przyjazna nazwa wyświetlana w nagłówku projektanta **PickBranch** . Wartość domyślna to gałąź.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Oznacza|Każda <xref:System.Activities.Statements.PickBranch> zawiera akcję <xref:System.Activities.Statements.PickBranch.Trigger%2A>, która może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Każda <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Action%2A>, które są wykonywane, jeśli wyzwolone.|

## <a name="see-also"></a>Zobacz też
 [Działanie pobrania](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [przepływu sterowania](../workflow-designer/control-flow-activity-designers.md) [przy użyciu działania pobrania](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)