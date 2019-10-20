---
title: Projektant przepływu pracy — Projektant działań PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650066"
---
# <a name="pickbranch-activity-designer"></a>PickBranch, projektant działań

@No__t_0 zapewnia ścieżkę wykonywania wykonywaną na podstawie zdarzeń w ramach działania <xref:System.Activities.Statements.Pick>, które mogą być wyzwalane przez zdarzenie przychodzące.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> obiekty są zawarte w kolekcji <xref:System.Activities.Statements.Pick.Branches%2A> działania <xref:System.Activities.Statements.Pick>. Każda <xref:System.Activities.Statements.PickBranch> jest zawarta w gałęzi działania <xref:System.Activities.Statements.Pick> i może być wykonywana z powodu zdarzenia przychodzącego, które służy jako wyzwalacz. W ten sposób Projektant przepływu pracy zapewnia modelowanie przepływu sterowania opartego na zdarzeniach. Każda <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać projektanta działań wyboru

Dostęp do projektanta **PickBranch** w kategorii **przepływ sterowania** w **przyborniku**.

Dwa puste obiekty <xref:System.Activities.Statements.PickBranch> z nazwami wyświetlanymi **Branch1** i **Branch2** są tworzone domyślnie jako elementy działania <xref:System.Activities.Statements.Pick>, gdy Projektant działań **wybierze** początkowo został porzucony w Projektant przepływu pracy. Te odpowiednie wartości właściwości <xref:System.Activities.Statements.PickBranch.DisplayName%2A> można edytować w nagłówku projektanta **PickBranch** lub w oknie **Właściwości** dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiektów do kolekcji obiektu <xref:System.Activities.Statements.Pick>: przeciąganie i upuszczanie projektanta **PickBranch** z **przybornika**lub za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy z poziomu obszaru projektowania **wyboru** :

- Projektant **PickBranch** tworzy <xref:System.Activities.Statements.PickBranch>, gdy jest przeciągany z **przybornika** i upuszczany do jednej z gałęzi projektanta działań **wyboru** na powierzchni Projektant przepływu pracy. Nowe obiekty <xref:System.Activities.Statements.PickBranch> mogą być umieszczane wewnątrz projektanta <xref:System.Activities.Statements.Pick> po lewej lub po prawej stronie wszelkich istniejących elementów <xref:System.Activities.Statements.PickBranch> już zawartych w kolekcji. Gdy przeciągasz projektanta **PickBranch** na projektanta **wyboru** z myszą, Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawane dla danego położenia myszy.

- Kliknij prawym przyciskiem myszy pozycję **Wybierz** projektanta działań (ale nie w programie **PickBranch** Designer), aby uzyskać menu kontekstowe i wybrać polecenie **Utwórz gałąź** , aby dodać nowe <xref:System.Activities.Statements.PickBranch>. Zwróć uwagę, że nowe <xref:System.Activities.Statements.PickBranch> są dodawane z prawej strony istniejących <xref:System.Activities.Statements.PickBranch> obiektów w projektancie **wyboru** .

Projektanta **PickBranch** można rozszerzyć, aby odsłonić pola **wyzwalacza** i **akcji** lub zwinięte przez kliknięcie podwójnego karetki po prawej stronie jego nagłówków. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> poszczególnych <xref:System.Activities.Statements.PickBranch> przez usunięcie działań do pól **wyzwalacz** i **Akcja** w swoich projektantach.

@No__t_0 obiektów w kolekcji <xref:System.Activities.Statements.Pick.Branches%2A> obiektu <xref:System.Activities.Statements.Pick>, można zmienić kolejność przez przeciąganie i upuszczanie ich do nowej lokalizacji w projektancie **wyboru** . Projektant **wyboru** używa pionowego szarego pasma, aby wskazać, gdzie <xref:System.Activities.Statements.PickBranch> jest dodawany dla danego położenia myszy.

Istnieją dwa sposoby usunięcia <xref:System.Activities.Statements.PickBranch>:

- Wybierz projektanta **PickBranch** i usuń go.
- Wybierz projektanta **PickBranch** , kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe, a następnie wybierz pozycję **Usuń**.

Pamiętaj, aby wybrać projektanta **PickBranch** , wybierając jedno z działań wewnątrz jego **wyzwalacza** lub **akcji** przez pomyłkę powoduje usunięcie jednej z tych działań, a nie obiektu <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektant przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości i opisano sposób ich używania w Projektant przepływu pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Przyjazna nazwa wyświetlana w nagłówku projektanta **PickBranch** . Wartość domyślna to gałąź.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Oznacza|Każda <xref:System.Activities.Statements.PickBranch> zawiera akcję <xref:System.Activities.Statements.PickBranch.Trigger%2A>, która może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Każda <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Action%2A>, które są wykonywane, jeśli wyzwolone.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)