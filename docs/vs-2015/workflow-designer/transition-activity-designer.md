---
title: Projektant działań przejścia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 446a78e706e1ba3cfd650418a9d329b62b330de8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606923"
---
# <a name="transition-activity-designer"></a>Transition, projektant działań
@No__t_0 reprezentuje przejście między dwoma stanami.

## <a name="using-the-transition-activity-designer"></a>Korzystanie z projektanta działań przejścia
 Projektant działań przejścia umożliwia skonfigurowanie przejścia między dwoma stanami.

### <a name="transition-properties-in-the-workflow-designer"></a>Właściwości przejścia w Projektant przepływu pracy
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Transition>, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Określa przyjazną nazwę projektanta działań <xref:System.Activities.Statements.Transition>. Wartość domyślna to **T1**. Wartość można edytować w siatce właściwości, w nagłówku rozwiniętego projektanta przejścia i w nagłówku sekcji akcji w rozwiniętym projektancie przejścia. @No__t_0 jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Jeśli jest obecny, określa wyrażenie, które musi oszacować **wartość true** przed przekazaniem kontroli do stanu docelowego. Ten warunek można edytować w siatce właściwości i w rozwiniętym projektancie przejścia. Wiele warunków w przejściu współdzielonym są oceniane w kolejności, w jakiej są wyświetlane w projektancie przejścia. **Uwaga:**  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia ma **wartość false** (lub wszystkie warunki przejścia wyzwalacza udostępnionego są oceniane na **Fałsz**), przejście nie zostanie wykonane, a wszystkie wyzwalacze dla wszystkich przejść ze stanu zostaną ponownie zaplanowane. W tym samouczku ta sytuacja nie może wystąpić ze względu na sposób skonfigurowania warunków (istnieją określone akcje dotyczące tego, czy wartość dopuszczalna jest poprawna czy niepoprawna).|
|**Zewnętrz**|Oznacza|Wskazuje stan, z którego pochodzi to przejście. Kliknięcie nazwy stanu źródła powoduje przełączenie widoku projektanta do rozwiniętego widoku tego stanu. Ta wartość jest ustawiana podczas tworzenia przejścia i nie można jej zmienić.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Określa działanie, którego zakończenie powoduje zainicjowanie przejścia. Aby ustawić to działanie, przeciągnij działanie z **przybornika** i upuść je na sekcję **wyzwalacz** przejścia.|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Określa działanie, które jest wykonywane po zakończeniu działania wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku **wartość true**. To działanie jest wykonywane podczas przejścia do stanu docelowego po wykonaniu <xref:System.Activities.Statements.State.Exit%2A> działania dla stanu źródła, jeśli jest obecny. Gdy projektant przejścia jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczenie go do sekcji **akcji** przejścia. Może istnieć wiele akcji dla jednego przejścia. Poszczególne akcje mogą być rozwinięte i uporządkowane. można je porządkować, klikając strzałkę w górę lub w dół, która pojawia się na akcji, gdy istnieje wiele akcji w przejściu.|
|**Punktu**|Oznacza|Wskazuje stan, do którego komputer stanu przechodzi po zakończeniu przejścia. Odpowiada właściwości <xref:System.Activities.Statements.Transition.To%2A> przejścia w modelu obiektów. Kliknięcie nazwy stanu docelowego powoduje przełączenie widoku projektanta do rozwiniętego widoku tego stanu. Ta wartość jest ustawiana podczas tworzenia przejścia i można ją zmienić, przeciągając strzałkę, która łączy przejście do stanu docelowego w projektancie.|

### <a name="creating-transitions"></a>Tworzenie przejść
 Przejścia są tworzone przez przeciąganie linii z jednego stanu do innego lub przez porzucenie stanu do trójkątów, które pojawiają się po przeciągnięciu jednego stanu do innego stanu. Aby utworzyć przejście przez przeciąganie, przesuń wskaźnik myszy nad brzeg stanu źródłowego i przeciągnij wiersz ze stanu źródłowego do stanu docelowego. Aby utworzyć przejście przez upuszczenie, przeciągnij stan docelowy i umieść go nad stanem źródłowym i upuść je na jednym z czterech trójkątów, które są wyświetlane wokół stanu źródłowego. Stan docelowy może być nowym stanem przeciąganym z **przybornika**lub istniejącym stanem przeciąganym z projektanta przepływu pracy.

> [!NOTE]
> Pojedynczy stan na komputerze stanu może obejmować maksymalnie 76 przejść utworzonych przy użyciu projektanta przepływu pracy. Limit przejść dla stanu dla przepływów pracy utworzonych poza projektantem jest ograniczony tylko przez zasoby systemowe.

 Przejścia wyzwalacza udostępnionego to zestaw przejść, które współużytkują to samo zdarzenie wyzwalacza. Wyzwalacz współużytkowany umożliwia warunkowe postęp do stanu docelowego na podstawie oceny wyrażeń skonfigurowanych dla wielu przejść, które współużytkują typowe zdarzenie wyzwalacza. Aby dodać kolejne akcje do przejścia i utworzyć wspólne przejście, kliknij kółko wskazujące początek żądanego przejścia i przeciągnij je do żądanego stanu. Nowe przejście spowoduje udostępnienie tego samego wyzwalacza co początkowe przejście, ale będzie miało unikatowy warunek i akcję. Współużytkowane przejścia można także utworzyć z poziomu projektanta przejścia, klikając pozycję **Dodaj przechodzenie wyzwalacza udostępnionego** u dołu projektanta przejścia, a następnie wybierając żądany stan docelowy z **dostępnych Stanów do połączenia** Lista rozwijana.

## <a name="see-also"></a>Zobacz też
 [](../workflow-designer/statemachine-activity-designer.md) [](../workflow-designer/finalstate-activity-designer.md) [Stan](../workflow-designer/state-activity-designer.md) FinalState StateMachine