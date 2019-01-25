---
title: Działania przepływu pracy w starszej wersji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa5a6da8d45435fc7c755905a19e95e90a98ad57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802386"
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji
[!INCLUDE[wf](../includes/wf-md.md)] zawiera domyślny zestaw działań, które zapewniają funkcje przepływu sterowania, warunki, obsługa zdarzeń, zarządzanie stanem i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy, można użyć działań dostarczane przez system, które są dostarczane przez [!INCLUDE[wfd1](../includes/wfd1-md.md)], lub możesz utworzyć własne niestandardowe działania.  
  
 W poniższej tabeli wymieniono [!INCLUDE[wf2](../includes/wf2-md.md)] zestawu działań out-of-box framework. Wiele, ale nie wszystkie te działania są reprezentowane przez projektantów działań, które mogą być udostępniane z **przybornika** z [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść je na powierzchni projektowej.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Używane z **działanie HandleExternalEventActivity** działania dla danych wejściowych i wyjściowych komunikacji z lokalną usługą. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Zawiera logikę oczyszczania dla działania złożonego anulowana, zanim wszystkie złożone działania podrzędne zostały zakończone wykonywania. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Umożliwia dodanie kodu języka Visual Basic lub C# do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Możliwy do kompensacji wersję [to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Możliwy do kompensacji wersję **działania TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Pozwala wywoływać kod, aby cofnąć lub kompensacji operacje już wykonywane przez przepływ pracy po wystąpieniu błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Otoka dla jednego lub kilku działań, które wykonują wynagrodzenia dla ukończonego działania działania TransactionScopeActivity [!INCLUDE[crdefault](../includes/crdefault-md.md)] [przy użyciu działania CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Wykonuje działania podrzędne, w oparciu o warunek, który ma zastosowanie do [grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) działania i na podstawie warunków, które są stosowane osobno do każdego elementu podrzędnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Umożliwia tworzenie opóźnienia w przepływie pracy, które są oparte na interwał limitu czasu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Opakowuje jedno lub wiele działań, które są wykonywane, gdy wystąpi określone zdarzenie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Zapewnia ramy pozwalające kojarzenie zdarzeń z działaniem. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Wykonuje jego działanie główny-podrzędny równocześnie z [działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Używane do obsługi wyjątku typu, który określisz. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Reprezentuje złożone działania, które jest uporządkowaną listą działania podrzędne typu [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[Działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Używany w połączeniu z [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) działania dla danych wejściowych i wyjściowych komunikacji z lokalną usługą. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Sprawdza warunek w każdej gałęzi i wykonuje działania na pierwszej gałęzi, dla której warunek ma wartość **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Reprezentuje gałęzi [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Włącza przepływ pracy do wywołania usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działaniu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Włącza przepływ pracy do wywołania inny przepływ pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Działanie złożone, który zawiera tylko [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) działania podrzędne. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Zapewnia sposób planowania dwóch lub więcej podrzędnych **to SequenceActivity** gałęzie działań do przetworzenia w tym samym czasie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działaniu równoległym](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Służy do reprezentowania kolekcji reguł. Reguła zawiera warunki i akcje wynikowe. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Tworzy wiele wystąpień działania pojedynczy element podrzędny. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[To SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Zapewnia to prosty sposób łączenia wielu działań razem dla wykonywania sekwencyjnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejścia do nowego stanu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w przepływ pracy automatu stanów. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Używane w [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działanie jako kontener dla działania podrzędne, które są wykonywane podczas opuszczania **działanie StateActivity** działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Używane w [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działanie jako kontener dla działania podrzędne, które są wykonywane podczas wprowadzania **działanie StateActivity** działania. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Wstrzymuje działanie przepływu pracy, aby umożliwić interwencji w przypadku jakiegoś warunku błędu, który wymaga szczególnej uwagi. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Wykonuje zawarte działania sekwencyjnie w domenie zsynchronizowane. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Umożliwia natychmiastowe zakończenie operacji przepływu pracy w przypadku wystąpienia błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Umożliwia przechwytywanie wyjątków firm zgłoszony jako część procesu metadanych dla przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[Działanie TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Zapewnia ramy pozwalające transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [przy użyciu działania działania TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Umożliwia to modelowanie występowania błędów usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[Działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Odbiera dane z usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Odpowiada na żądanie usługi sieci Web, wprowadzone do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Za pomocą działania WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Włącza przepływ pracy w pętli do momentu spełnienia warunku. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Przy użyciu działania Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] sposób tworzenia działań niestandardowych, zobacz [opracowywania niestandardowych działań](http://go.microsoft.com/fwlink?LinkID=65023) i [przy użyciu starszej wersji projektanta działań](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Widoki działania (starsza wersja)](../workflow-designer/activity-views-legacy.md)  
 Zawiera opis widoków różnorodności działań.  
  
 [Instrukcje: Dodawanie działań do przybornika (starsza wersja)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Przedstawiono sposób dodawania działań do przybornika.  
  
 [Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Przedstawia kroki tworzenia warunku reguły deklaratywnej.  
  
 [Instrukcje: Tworzenie zestawu reguł działania PolicyActivity (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Przedstawia kroki, aby utworzyć zestaw reguł działania PolicyActivity.  
  
 [Instrukcje: Implementowanie operacji kontraktu usługi WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Przedstawia kroki, aby wdrożyć [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontrakt operacji.  
  
 [Instrukcje: Wywoływanie operacji kontraktu usługi WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Przedstawia kroki, aby wywołać [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontrakt operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Działania związane z Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Tworzenie przepływów pracy](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Tworzenie działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65023)