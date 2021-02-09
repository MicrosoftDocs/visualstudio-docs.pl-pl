---
title: Projektant przepływu pracy — Projektant działań stanu
description: Dowiedz się więcej o działaniu StateMachine i sposobach dodawania stanu do przepływu pracy za pomocą projektanta działań stanu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873518"
---
# <a name="state-activity-designer"></a>State, projektant działań

<xref:System.Activities.Statements.State>Reprezentuje stan, w którym może znajdować się komputer stanu.

## <a name="using-the-state-activity-designer"></a>Korzystanie z programu Projektant działań stanu

Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij projektanta działań **stanu** z sekcji **stan automatu** w **przyborniku** i upuść go na <xref:System.Activities.Statements.StateMachine> działanie na Projektant przepływu pracy powierzchni. <xref:System.Activities.Statements.State>Działanie może zostać porzucone do <xref:System.Activities.Statements.StateMachine> i przejść dodane później; lub można utworzyć przejście, gdy <xref:System.Activities.Statements.State> działanie zostanie odrzucone. Aby dodać <xref:System.Activities.Statements.State> działanie i utworzyć przejście w jednym kroku, przeciągnij działanie **stanu** z sekcji **stan automatu** **przybornika** i umieść je w innym stanie w Projektancie przepływu pracy. Gdy przeciągany <xref:System.Activities.Statements.State> jest nad innym <xref:System.Activities.Statements.State> , cztery Trójkąty będą widoczne wokół siebie <xref:System.Activities.Statements.State> . Jeśli <xref:System.Activities.Statements.State> zostanie porzucone na jeden z czterech trójkątów, zostanie dodany do komputera stanu i zostanie utworzone przejście z lokalizacji źródłowej <xref:System.Activities.Statements.State> do porzuconego miejsca docelowego <xref:System.Activities.Statements.State> . Aby uzyskać więcej informacji, zobacz [Przechodzenie](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości działania stanu w Projektant przepływu pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.State> właściwości, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.State> projektanta działań w nagłówku. Wartość domyślna to **State**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań. Ta wartość <xref:System.Activities.Statements.State.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Chociaż <xref:System.Activities.Statements.State.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.State.Entry%2A>|Fałsz|Określa akcję, która występuje, gdy ten stan jest przenoszony do. Gdy <xref:System.Activities.Statements.State> działanie jest rozwinięte, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i usunięcie go do sekcji **wpis** stanu.|
|<xref:System.Activities.Statements.State.Exit%2A>|Fałsz|Określa akcję, która występuje, gdy ten stan zostanie przeniesiony z. Gdy <xref:System.Activities.Statements.State> działanie jest rozwinięte, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i usunięcie go do sekcji **wyjście** stanu.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Fałsz|Wyświetla listę możliwych przejść, które pochodzą z programu <xref:System.Activities.Statements.State> . Każdy element na liście ma link do skojarzonego <xref:System.Activities.Statements.Transition> i docelowego obiektu <xref:System.Activities.Statements.State> . Kliknięcie linku spowoduje przełączenie projektanta do rozwiniętego widoku <xref:System.Activities.Statements.Transition> lub <xref:System.Activities.Statements.State> .|

## <a name="see-also"></a>Zobacz też

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
