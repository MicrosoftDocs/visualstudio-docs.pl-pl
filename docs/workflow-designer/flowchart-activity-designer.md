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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597038"
---
# <a name="flowchart-activity-designer"></a>Flowchart, projektant działań

Działanie <xref:System.Activities.Statements.Flowchart> służy do tworzenia przepływów pracy, które definiują złożone kontrolki przepływu i zarządzają nimi. <xref:System.Activities.Statements.Flowchart> można tworzyć w kodzie lub przy użyciu Projektant przepływu pracy. W tym temacie opisano środowisko Projektant przepływu pracy. Projektant działań przepływu pracy Projektant przepływu pracy umożliwia deweloperom tworzenie przepływów pracy w naturalny sposób.

## <a name="the-flowchart-activity"></a>Działanie Flowchart

<xref:System.Activities.Statements.Flowchart> określa unikatowy <xref:System.Activities.Statements.Flowchart.StartNode%2A>, który jest wykonywany, gdy przepływ pracy zostanie uruchomiony i używa sieci połączonych <xref:System.Activities.Statements.Flowchart.Nodes%2A> do tworzenia dowolnych pętli lub do przepływu wykonania w dowolnym miejscu w przepływie pracy w dowolnym momencie.

### <a name="using-the-flowchart-activity-designer"></a>Korzystanie z projektanta działań Flowchart

Projektant działań **Flowchart** można znaleźć w kategorii **schemat blokowy** , do którego **uzyskuje się dostęp**, klikając kartę **Przybornik** na Projektant przepływu pracy. Alternatywnie wybierz pozycję **Przybornik** z menu **Widok** lub naciśnij **klawisze CTRL**+**Alt**+**X**.

Projektant działań **schematu blokowego** może być przeciągany z **przybornika** i upuszczany na Projektant przepływu pracy powierzchnię, gdy projektanci aktywności są zwykle umieszczane jako działania główne lub jako element podrzędny innego działania przepływu sterowania. Jeśli Projektant działań **Flowchart** zostanie porzucony na pustej powierzchni Projektant przepływu pracy, tworzy działanie <xref:System.Activities.Statements.Flowchart>, które domyślnie prezentuje się w rozwiniętym widoku, w którym węzeł początkowy inicjujący wykonywanie jest reprezentowany jako Zielona kulka. Jeśli Projektant działań **schematu blokowego** zostanie porzucony w innym działaniu przepływu sterowania, zostanie on wyświetlony w widoku zminimalizowanym, który można rozszerzyć przez dwukrotne kliknięcie projektanta działań **schematu blokowego** . Wszystkie działania w **przyborniku** można przeciągnąć bezpośrednio do projektanta działań **schematu blokowego** , łącznie z innymi działaniami przepływu sterowania.

Po przeciągnięciu różnych projektantów działań na kanwę Projektant przepływu pracy obiekty <xref:System.Activities.Activity>, które reprezentują, mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między aktywnością źródłową a działaniem docelowym, wskaźnik myszy nad projektantem działania źródłowego i kwadratowe uchwyty pojawiają się po każdej stronie. Kliknij jeden z uchwytów kwadratowych i przeciągnij go, przytrzymując wciśnięty przycisk myszy do jednego z uchwytów, które pojawiają się w podobny sposób wokół działania docelowego po umieszczeniu na nim wskaźnika myszy. Zwolnij przycisk myszy i Utwórz link między tymi dwoma działaniami, które są reprezentowane jako strzałka z projektanta źródła do docelowego projektanta.

### <a name="flowchart-activity-properties"></a>Właściwości działania Flowchart

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Flowchart> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektanta.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to Flowchart. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Fałsz|Kolekcja zmiennych, które są objęte zakresem w ramach tej <xref:System.Activities.Statements.Flowchart>, aby udostępnić stan w ramach działań podrzędnych.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Fałsz|<xref:System.Activities.Statements.FlowNode>, który jest wykonywany podczas uruchamiania <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Fałsz|Zawiera kolekcję obiektów <xref:System.Activities.Statements.FlowNode> w <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
