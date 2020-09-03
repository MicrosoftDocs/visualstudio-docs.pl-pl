---
title: Projektant przepływu pracy — Projektant działań schematu blokowego
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d786e9acfa99d2b106b72822a0106e2161724790
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597038"
---
# <a name="flowchart-activity-designer"></a>Flowchart, projektant działań

To <xref:System.Activities.Statements.Flowchart> działanie służy do tworzenia przepływów pracy, które definiują złożone kontrolki przepływu i zarządzają nimi. <xref:System.Activities.Statements.Flowchart>Można tworzyć w kodzie lub przy użyciu Projektant przepływu pracy. W tym temacie opisano środowisko Projektant przepływu pracy. Projektant działań przepływu pracy Projektant przepływu pracy umożliwia deweloperom tworzenie przepływów pracy w naturalny sposób.

## <a name="the-flowchart-activity"></a>Działanie Flowchart

<xref:System.Activities.Statements.Flowchart>Określa unikatowy <xref:System.Activities.Statements.Flowchart.StartNode%2A> , który jest wykonywany podczas uruchamiania przepływu pracy i korzysta z sieci połączonej <xref:System.Activities.Statements.Flowchart.Nodes%2A> w celu utworzenia dowolnych pętli lub do przepływu wykonywania w dowolnym miejscu w przepływie pracy w dowolnym momencie.

### <a name="using-the-flowchart-activity-designer"></a>Korzystanie z projektanta działań Flowchart

Projektant działań **Flowchart** można znaleźć w kategorii **schemat blokowy** , do którego **uzyskuje się dostęp**, klikając kartę **Przybornik** na Projektant przepływu pracy. Alternatywnie możesz wybrać **Przybornik** z menu **Widok** lub nacisnąć **klawisze CTRL** + **Alt** + **X**.

Projektant działań **schematu blokowego** może być przeciągany z **przybornika** i upuszczany na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane jako działania główne lub jako element podrzędny innego działania przepływu sterowania. Jeśli Projektant działań **Flowchart** zostanie porzucony na pustej powierzchni Projektant przepływu pracy, tworzy <xref:System.Activities.Statements.Flowchart> działanie, które domyślnie prezentuje się w rozwiniętym widoku, w którym węzeł początkowy inicjujący wykonywanie jest reprezentowany jako Zielona kulka. Jeśli Projektant działań **schematu blokowego** zostanie porzucony w innym działaniu przepływu sterowania, zostanie on wyświetlony w widoku zminimalizowanym, który można rozszerzyć przez dwukrotne kliknięcie projektanta działań **schematu blokowego** . Wszystkie działania w **przyborniku** można przeciągnąć bezpośrednio do projektanta działań **schematu blokowego** , łącznie z innymi działaniami przepływu sterowania.

Po przeciągnięciu różnych projektantów działań na kanwę Projektant przepływu pracy <xref:System.Activities.Activity> obiekty, które reprezentują, mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między aktywnością źródłową a działaniem docelowym, wskaźnik myszy nad projektantem działania źródłowego i kwadratowe uchwyty pojawiają się po każdej stronie. Kliknij jeden z uchwytów kwadratowych i przeciągnij go, przytrzymując wciśnięty przycisk myszy do jednego z uchwytów, które pojawiają się w podobny sposób wokół działania docelowego po umieszczeniu na nim wskaźnika myszy. Zwolnij przycisk myszy i Utwórz link między tymi dwoma działaniami, które są reprezentowane jako strzałka z projektanta źródła do docelowego projektanta.

### <a name="flowchart-activity-properties"></a>Właściwości działania Flowchart

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Flowchart> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to Flowchart. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Fałsz|Kolekcja zmiennych, które są objęte zakresem, <xref:System.Activities.Statements.Flowchart> Aby udostępnić stan w ramach działań podrzędnych.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Fałsz|<xref:System.Activities.Statements.FlowNode>Jest wykonywane po <xref:System.Activities.Statements.Flowchart> uruchomieniu.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Fałsz|Zawiera kolekcję <xref:System.Activities.Statements.FlowNode> obiektów w obiekcie <xref:System.Activities.Statements.Flowchart> .|

## <a name="see-also"></a>Zobacz też

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
