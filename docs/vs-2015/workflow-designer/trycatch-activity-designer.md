---
title: TryCatch, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9d8c539d91c95b03f4946e256de7a825a6df7ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976609"
---
# <a name="trycatch-activity-designer"></a>TryCatch, projektant działań
**TryCatch** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TryCatch> działania.  
  
## <a name="the-trycatch-activity"></a>Działania TryCatch  
 <xref:System.Activities.Statements.TryCatch> Zawiera działanie <xref:System.Activities.Statements.TryCatch.Try%2A> aktywności, zbiór **Catch\<TException >** i <xref:System.Activities.Statements.TryCatch.Finally%2A> działania. A <xref:System.Activities.Statements.Catch%601> typu **TException** zawiera <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> i <xref:System.Activities.Statements.Catch%601.Action%2A>. Służą one ze sobą do zaimplementowania typowych opartą na wyjątkach mechanizm obsługi błędów. A <xref:System.Activities.Statements.TryCatch> działania próbuje wykonać jego <xref:System.Activities.Statements.TryCatch.Try%2A> działania. Jeśli <xref:System.Activities.Statements.TryCatch.Try%2A> działania generuje każdy wyjątek <xref:System.Activities.Statements.TryCatch> używa działanie jego **Catch < TException\>**  kolekcji, aby dopasować wyjątku. Jeśli istnieje dopasowanie, a następnie <xref:System.Activities.Statements.Catch%601.Action%2A> odpowiadającego **Catch\<TException >** jest wykonywane, służąc jako logiki, dla wyjątku obsługi błędów. Jeśli działania w <xref:System.Activities.Statements.TryCatch.Try%2A> sekcji zostało ukończone pomyślnie, lub działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> zostało ukończone pomyślnie, <xref:System.Activities.Statements.TryCatch> wykonuje działanie jego <xref:System.Activities.Statements.TryCatch.Finally%2A> działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Wyjątki](http://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).  
  
### <a name="using-the-trycatch-activity-designer"></a>Za pomocą TryCatch, Projektant działań  
 **TryCatch** projektanta działań można znaleźć w **obsługę błędów** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty w lewej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub TROLERA + ALT + X.)  
  
 **TryCatch** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TryCatch> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z TryCatch. <xref:System.Activities.Activity.DisplayName%2A> Wartość może być edytowana w nagłówku **TryCatch** projektanta działań lub **DisplayName** pola siatki właściwości. Inne właściwości, należy edytować na powierzchni **TryCatch** projektanta działań.  
  
 Kliknij przycisk rozwijania w prawym górnym rogu **TryCatch** projektanta, aby zobaczyć **spróbuj**, **przechwytuje**, i **na koniec** pól rozwinięty widok. Aby dodać bloku catch, kliknij **Dodaj nowe catch** znajdujący się na **TryCatch** projektanta. Przycisk zmienia pole kombi typu. Wybierz typ wyjątku, a następnie naciśnij klawisz ENTER, aby dodać catch. Po dodaniu **Catch**rozwija obszar catch i działania można upuszczać WE catch, aby zdefiniować logikę wykonywania catch. Zwróć uwagę, że pola tekstowego po prawej stronie obszaru rozwiniętej catch. Możesz nazwać zmienną wyjątków za pomocą tego pola tekstowego. Zmienna wyjątków należy używać tylko dla działań w tym samym **Catch**.  
  
 **TryCatch** Projektant nie obsługuje edytowania **Catch**. Jeśli chcesz zmienić typ wyjątku, musisz usunąć **Catch** i dodania nowego. A **Catch** można je usunąć, wybierając ją i usunięcie go lub za pomocą **Usuń** menu w menu kontekstowym, dostępnego po kliknięciu prawym przyciskiem myszy.  
  
### <a name="the-trycatch-properties"></a>Właściwości TryCatch  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TryCatch>właściwości i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa opcjonalny przyjazna nazwa <xref:System.Activities.Statements.TryCatch> działania. Wartość domyślna to TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Działanie pierwszego wykonania, kiedy <xref:System.Activities.Statements.TryCatch> wykonuje.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Kolekcja **Catch** elementów do sprawdzenia, kiedy <xref:System.Activities.Statements.TryCatch.Try%2A> działanie zgłasza wyjątek.<br /><br /> Dodaj potrzebne co najmniej jednym działaniem <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Działanie do wykonania, gdy <xref:System.Activities.Statements.TryCatch.Try%2A> oraz wszelkie niezbędne działania w <xref:System.Activities.Statements.TryCatch.Catches%2A> ukończenie kolekcji.<br /><br /> Dodaj potrzebne co najmniej jednym działaniem <xref:System.Activities.Statements.TryCatch.Catches%2A> lub działania w <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)   
 [Zgłoś ponownie](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)