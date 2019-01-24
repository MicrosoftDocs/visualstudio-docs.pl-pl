---
title: Przejście do projektanta działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69e918eae56d35d134b9b7c3093d5f0599a12c5e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760317"
---
# <a name="transition-activity-designer"></a>Transition, projektant działań
A <xref:System.Activities.Statements.Transition> reprezentuje przejścia między dwoma stanami.  
  
## <a name="using-the-transition-activity-designer"></a>Za pomocą Transaction, Projektant działań  
 Transaction, Projektant działań umożliwia skonfigurowanie przejścia między dwoma stanami.  
  
### <a name="transition-properties-in-the-workflow-designer"></a>Właściwości przejścia w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Transition> właściwości, które można ustawić za pomocą projektanta przepływów pracy i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Transition> projektanta działań. Wartość domyślna to **T1**. Wartość można edytować w siatce właściwości w nagłówku projektanta przejścia rozwinięty i w nagłówku sekcji akcja w Projektancie rozwiniętej przejścia. <xref:System.Activities.Activity.DisplayName%2A> Jest używany w nadrzędnych, która jest wyświetlana w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Jeśli jest obecny, określa wyrażenie, które musi zwrócić **True** zanim sterowanie jest przekazywane do stanu docelowego. Tego warunku można edytować w siatce właściwości i w Projektancie rozwiniętej przejścia. Wiele warunków w udostępnionym przejścia są obliczane w kolejności, w jakiej występują w Projektancie przejścia. **Uwaga:**  Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku **False** (lub zwrócić wszystkie warunki przejścia udostępnionego wyzwalacza **False**), nie nastąpi przejście i wszystkich wyzwalaczy dla wszystkich powoduje zmianę planu przejścia ze stanu. W tym samouczku ta sytuacja nie może się zdarzyć, ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).|  
|**Element źródłowy**|Prawda|Wskazuje stan, z którego pochodzi ten proces przejścia. Klikając nazwę stanu źródła przełącza widok projektanta do rozwinięty widok tego stanu. Ta wartość jest ustawiona, gdy przejście zostanie utworzona i nie można jej zmienić.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Określa działanie, którego ukończenie inicjuje przejścia. Aby ustawić to działanie, przeciągnij działanie z **przybornika** i upuść je na **wyzwalacza** sekcji przejścia.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Określa działania, który jest wykonywany po zakończeniu działania wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku **true**. To działanie jest wykonywany, gdy przechodzi do stanu docelowego po <xref:System.Activities.Statements.State.Exit%2A> stanu źródła, jeśli jest obecny, jest wykonywane działanie. Po rozwinięciu projektanta przejścia tę wartość można ustawić, przeciągając działanie w **przybornika** i upuszczając go na **akcji** sekcji przejścia. Może istnieć wiele akcji dla jednego przejścia. Poszczególne akcje można rozszerzyć i nabytej i może zostać określona przez kliknięcie przycisku w górę lub w dół strzałki, który pojawia się na akcję w przypadku wielu akcji w okresie przejściowym.|  
|**miejsce docelowe**|Prawda|Wskazuje stan, który przechodzi automatu stanów, po zakończeniu przejścia. Odpowiada to <xref:System.Activities.Statements.Transition.To%2A> właściwość przejścia w modelu obiektów. Klikając nazwę stanu docelowego przełącza widok projektanta do rozwinięty widok tego stanu. Ta wartość jest ustawiona, gdy przejście zostanie utworzona i można zmienić, przeciągając strzałkę, która łączy przejście do stanu docelowego w projektancie.|  
  
### <a name="creating-transitions"></a>Tworzenie przejścia  
 Przejścia są tworzone przez przeciąganie linii z jednego stanu do innego lub odrzucając stan na trójkąty, które są wyświetlane, gdy jeden stan jest przeciągany nad inny stan. Aby utworzyć przejście przez przeciąganie, umieść kursor myszy nad krawędzi stanu źródła i przeciągnij linię od stanu źródłowego do stanu docelowego. Aby utworzyć przejście przez porzucenie, przeciągnij stan docelowy kursor stanu źródła i upuść go na jeden z czterech trójkątów, które pojawiają się wokół stanu źródła. Stan docelowy może być albo nowy stan przeciągnięte z **przybornika**, lub istniejący stan przeciągnięte z projektanta przepływów pracy.  
  
> [!NOTE]
>  Pojedynczy stan w automacie stanów może mieć maksymalnie 76 przejścia utworzone za pomocą projektanta przepływów pracy. Limit przejścia dla stanu utworzony poza projektanta przepływów pracy jest ograniczony tylko ilością zasobów systemowych.  
  
 Udostępnione wyzwalacza przejścia są zestawu przejść, które mają te same zdarzenia wyzwalacza. Wyzwalacz udostępnionego umożliwia warunkowego przejście do stanu docelowego, na podstawie oceny wyrażenia skonfigurowane dla wielu przejścia, które mają wspólne zdarzenie wyzwalacza. Aby dodać dodatkowe akcje do przejścia i tworzenia udostępnionych przejść, kliknij przycisk koła, który wskazuje początek żądanego przejścia i przeciągnij go do żądanego stanu. Nowe przejście współużytkują tego samego wyzwalacza jako przejściu początkowym, ale będzie mieć unikatowy warunków i akcji. Udostępnione przejścia można również utworzyć z w Projektancie przejścia, klikając **Dodaj udostępnionych przejść wyzwalaczy** w dolnej części projektanta przejścia, a następnie wybierając stanu wybraną docelową z  **Stany połączyć** listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Automat stanów](../workflow-designer/statemachine-activity-designer.md)   
 [Stan końcowy](../workflow-designer/finalstate-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)