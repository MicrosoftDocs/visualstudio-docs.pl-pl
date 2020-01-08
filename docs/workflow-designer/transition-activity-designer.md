---
title: Projektant przepływu pracy — Projektant działań przejścia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: c71f31f4582a60bcfc87e4906a1447e33ffa7bd3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593086"
---
# <a name="transition-activity-designer"></a>Transition, projektant działań

<xref:System.Activities.Statements.Transition> reprezentuje przejście między dwoma stanami.

## <a name="using-the-transition-activity-designer"></a>Korzystanie z projektanta działań przejścia

Projektant działań przejścia umożliwia skonfigurowanie przejścia między dwoma stanami.

### <a name="transition-properties-in-the-workflow-designer"></a>Właściwości przejścia w Projektant przepływu pracy

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.Transition>, które można ustawić za pomocą projektanta przepływów pracy, i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Fałsz|Określa przyjazną nazwę projektanta działań <xref:System.Activities.Statements.Transition>. Wartość domyślna to **T1**. Wartość można edytować w siatce właściwości, w nagłówku rozwiniętego projektanta przejścia i w nagłówku sekcji akcji w rozwiniętym projektancie przejścia. <xref:System.Activities.Activity.DisplayName%2A> jest używana w nawigacyjnym nawigacji, który jest wyświetlany w górnej części projektanta przepływu pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Fałsz|Jeśli jest obecny, określa wyrażenie, które musi oszacować **wartość true** przed przekazaniem kontroli do stanu docelowego. Ten warunek można edytować w siatce właściwości i w rozwiniętym projektancie przejścia. Wiele warunków w przejściu współdzielonym są oceniane w kolejności, w jakiej są wyświetlane w projektancie przejścia. **Uwaga:**  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia ma **wartość false** (lub wszystkie warunki przejścia wyzwalacza udostępnionego są oceniane na **Fałsz**), przejście nie zostanie wykonane, a wszystkie wyzwalacze dla wszystkich przejść ze stanu zostaną ponownie zaplanowane. W tym samouczku ta sytuacja nie może wystąpić ze względu na sposób skonfigurowania warunków (istnieją określone akcje dotyczące tego, czy wartość dopuszczalna jest poprawna czy niepoprawna).|
|**Element źródłowy**|Prawda|Wskazuje stan, z którego pochodzi to przejście. Kliknięcie nazwy stanu źródła powoduje przełączenie widoku projektanta do rozwiniętego widoku tego stanu. Ta wartość jest ustawiana podczas tworzenia przejścia i nie można jej zmienić.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Fałsz|Określa działanie, którego zakończenie powoduje zainicjowanie przejścia. Aby ustawić to działanie, przeciągnij działanie z **przybornika** i upuść je na sekcję **wyzwalacz** przejścia.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Fałsz|Określa działanie, które jest wykonywane po zakończeniu działania wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku **wartość true**. To działanie jest wykonywane podczas przejścia do stanu docelowego po wykonaniu <xref:System.Activities.Statements.State.Exit%2A> działania dla stanu źródła, jeśli jest obecny. Gdy projektant przejścia jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczenie go do sekcji **akcji** przejścia. Może istnieć wiele akcji dla jednego przejścia. Poszczególne akcje mogą być rozwinięte i uporządkowane. można je porządkować, klikając strzałkę w górę lub w dół, która pojawia się na akcji, gdy istnieje wiele akcji w przejściu.|
|**Punktu**|Prawda|Wskazuje stan, do którego komputer stanu przechodzi po zakończeniu przejścia. Odpowiada właściwości <xref:System.Activities.Statements.Transition.To%2A> przejścia w modelu obiektów. Kliknięcie nazwy stanu docelowego powoduje przełączenie widoku projektanta do rozwiniętego widoku tego stanu. Ta wartość jest ustawiana podczas tworzenia przejścia i można ją zmienić, przeciągając strzałkę, która łączy przejście do stanu docelowego w projektancie.|

### <a name="creating-transitions"></a>Tworzenie przejść

Przejścia są tworzone przez przeciąganie linii z jednego stanu do innego lub przez porzucenie stanu do trójkątów, które pojawiają się po przeciągnięciu jednego stanu do innego stanu. Aby utworzyć przejście przez przeciąganie, przesuń wskaźnik myszy nad brzeg stanu źródłowego i przeciągnij wiersz ze stanu źródłowego do stanu docelowego. Aby utworzyć przejście przez upuszczenie, przeciągnij stan docelowy i umieść go nad stanem źródłowym i upuść je na jednym z czterech trójkątów, które są wyświetlane wokół stanu źródłowego. Stan docelowy może być nowym stanem przeciąganym z **przybornika**lub istniejącym stanem przeciąganym z projektanta przepływu pracy.

> [!NOTE]
> Pojedynczy stan na komputerze stanu może obejmować maksymalnie 76 przejść utworzonych przy użyciu projektanta przepływu pracy. Limit przejść dla stanu dla przepływów pracy utworzonych poza projektantem jest ograniczony tylko przez zasoby systemowe.

Przejścia wyzwalacza udostępnionego to zestaw przejść, które współużytkują to samo zdarzenie wyzwalacza. Wyzwalacz współużytkowany umożliwia warunkowe postęp do stanu docelowego na podstawie oceny wyrażeń skonfigurowanych dla wielu przejść, które współużytkują typowe zdarzenie wyzwalacza. Aby dodać kolejne akcje do przejścia i utworzyć wspólne przejście, kliknij kółko wskazujące początek żądanego przejścia i przeciągnij je do żądanego stanu. Nowe przejście spowoduje udostępnienie tego samego wyzwalacza co początkowe przejście, ale będzie miało unikatowy warunek i akcję. Współużytkowane przejścia można także utworzyć z poziomu projektanta przejścia, klikając pozycję **Dodaj przechodzenie wyzwalacza udostępnionego** u dołu projektanta przejścia, a następnie wybierając żądany stan docelowy z listy rozwijanej **dostępne Stany do połączenia** .

## <a name="see-also"></a>Zobacz także

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Stan](../workflow-designer/state-activity-designer.md)
