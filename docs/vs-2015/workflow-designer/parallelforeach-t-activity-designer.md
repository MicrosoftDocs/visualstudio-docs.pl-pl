---
title: ParallelForEach&lt;T&gt; projektanta działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 825906f3de1b2d40d96dc19ed45d2a368d889994
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002308"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.ParallelForEach%601> Działanie wylicza elementów kolekcji i wykonuje osadzonych instrukcji dla każdego elementu kolekcji równolegle, co jest asynchronicznie, w tym samym wątku. Użyj tego działania przepływu sterowania, zamiast <xref:System.Activities.Statements.Sequence> działania, jeśli działania podrzędne działania powinny przejść w stanie bezczynności.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> Działanie ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> właściwość, która zawiera określone przez użytkownika [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenia. <xref:System.Activities.Statements.ParallelForEach%601> Działania daje w wyniku tej właściwości po zakończeniu każdej gałęzi. Jeśli daje w wyniku **true**, a następnie <xref:System.Activities.Statements.ParallelForEach%601> działanie zakończy się bez wykonania innych działów. Jeśli <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nie można rozpoznać **true**, a następnie <xref:System.Activities.Statements.ParallelForEach%601> ukończeniu działania, gdy wszystkie działania podrzędne zostały ukończone.  
  
## <a name="the-parallelforeacht-activity"></a>ParallelForEach\<T > działania  
 <xref:System.Activities.Statements.ParallelForEach%601> Wylicza jego wartościami i harmonogramy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> dla każdej wartości wylicza na. Tylko planuje <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Jak wykonuje treść jest zależna od tego, czy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> przechodzi w stanie bezczynności.  
  
 Jeśli <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nie przechodzi bezczynny, wykonuje w odwrotnej kolejności ponieważ zaplanowanych działań są obsługiwane jako stosu, najpierw wykonana ostatnim zaplanowanym działaniem. Na przykład, jeśli masz kolekcję {1,2,3,4}w <xref:System.Activities.Statements.ParallelForEach%601> i użyj **WriteLine** jako treść do zapisu wartości. Masz 4, 3, 2, 1 drukowane w konsoli. Jest to spowodowane **WriteLine** nie przechodzi bezczynności, więc po 4 **WriteLine** stało się zaplanowane działania, ich posługując się działanie stosu (pierwszym w ostatniej out).  
  
 Ale w przypadku działania <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , można przejść bezczynny, takich jak <xref:System.ServiceModel.Activities.Receive> działania lub <xref:System.Activities.Statements.Delay> działania. Następnie nie ma potrzeby oczekiwania na ich zakończenie. <xref:System.Activities.Statements.ParallelForEach%601> zbliża się do następnego zaplanowane działania treści i spróbuj uruchomić go. Awaria działania bezczynności, <xref:System.Activities.Statements.ParallelForEach%601> przesuwa na ponownie następne działanie treści.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>Za pomocą ParallelForEach\<T > Projektant działań  
 **ParallelForEach\<T >** projektanta działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karty w lewej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **ParallelForEach\<T >** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie Projektanci działań są zazwyczaj umieszczone, dla przykład wewnątrz **sekwencji** projektanta działań. Po upuszczając go do [!INCLUDE[wfd2](../includes/wfd2-md.md)], tworzy on <xref:System.Activities.Statements.ParallelForEach%601> działania, które domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> z **ParallelForEach\<Int32 >.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > właściwości w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ParallelForEach%601> właściwości działania i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działań w nagłówku. Wartość domyślna to **ParallelForEach\<Int32 >**. Wartość może być opcjonalnie edytować w **właściwości** siatki lub bezpośrednio w nagłówku projektanta działań.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Działanie do wykonania dla każdego elementu w kolekcji. Można dodać <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> działania, listy działanie z przybornika do **treści** polu na **ParallelForEach\<T >** projektanta działań z tekst wskazówki "Upuść działanie tutaj".|  
|**TypeArgument**|Prawda|Typ elementów w <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> kolekcji określonej przez parametr ogólny *T*. Domyślnie **elementu typeargument w języku** ustawiono **Int32**. Aby zmienić typ T w **ParallelForEach\<T >** Projektant działań, zmień wartość właściwości **elementu typeargument w języku** pola kombi w siatce właściwości.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Prawda|Kolekcja elementów do iteracji. Aby ustawić <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, wpisz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] wyrażenia w **wartości** polu na **ForEach\<T >** projektanta działań w polu tekst wskazówki "Wprowadź wyrażenie VB" lub w **Wartości** polu na **właściwości** okna.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Oceniane, po zakończeniu każdej iteracji. Jeśli go daje w wyniku wartość true, a następnie zaplanowanych do czasu iteracji są anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie instrukcje zaplanowane wykonywanie aż do zakończenia.|  
  
 Domyślnie iteratora pętli nosi nazwę elementu. Można zmienić nazwy zmiennej iteratora w **ForEach** pole w **ParallelForEach\<T >** projektanta działań. Iteratora pętli można używać w wyrażeniach w elementy podrzędne <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Sekwencja](../workflow-designer/sequence-activity-designer.md)   
 [równoległe](../workflow-designer/parallel-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)