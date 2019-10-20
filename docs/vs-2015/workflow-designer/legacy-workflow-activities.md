---
title: Działania ze starszych przepływów pracy | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4f1110424aefc1771c0dc7600fb9996bff0e892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658938"
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji
[!INCLUDE[wf](../includes/wf-md.md)] zawiera domyślny zestaw działań, które zapewniają funkcjonalność przepływu sterowania, warunków, obsługi zdarzeń, zarządzania stanami i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy można korzystać z działań dostarczonych przez system [!INCLUDE[wfd1](../includes/wfd1-md.md)] lub można tworzyć własne działania niestandardowe.

 Poniższa tabela zawiera listę wstępnie ustawionych działań [!INCLUDE[wf2](../includes/wf2-md.md)] Framework. Wiele, ale nie wszystkie z tych działań, są reprezentowane przez projektantów działań, do których można uzyskać dostęp z **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść go na powierzchni projektowej.

|Działanie|Opis|
|--------------|-----------------|
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Używane z działaniem **HandleExternalEventActivity** dla komunikacji wejściowej i wyjściowej z usługą lokalną. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|[Działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Używany do przechowywania logiki oczyszczania dla działania złożonego anulowane przed ukończeniem wszystkich elementów podrzędnych działania złożonego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|[Elementu CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Umożliwia dodanie Visual Basic lub C# kodu do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania elementu CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Kompensowana wersja [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Kompensowana wersja elementów **TransactionScope**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|[Działania CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Umożliwia wywoływanie kodu w celu cofnięcia lub zrekompensowania operacji już wykonywanych przez przepływ pracy w przypadku wystąpienia błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działania CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Otoka dla jednej lub większej liczby działań, które wykonują kompensację ukończonego działania TransactionScope, [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Wykonuje działania podrzędne na podstawie warunku, który ma zastosowanie do działania [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) , i na podstawie warunków, które są stosowane oddzielnie dla każdego elementu podrzędnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|[Opóźnienie](http://go.microsoft.com/fwlink?LinkID=65028)|Umożliwia tworzenie opóźnień w przepływie pracy, które są oparte na interwale limitów czasu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Opóźnij](http://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Zawija jedno lub więcej działań, które są wykonywane po wystąpieniu określonego zdarzenia. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Udostępnia strukturę służącą do kojarzenia zdarzeń z działaniem. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Wykonuje swoje główne działanie podrzędne współbieżnie przy użyciu [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|[Działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Używane do obsługi wyjątku określonego typu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Reprezentuje działanie złożone, które ma uporządkowaną listę działań podrzędnych typu [działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Używane w połączeniu z działaniem [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) dla komunikacji wejścia i wyjścia z usługą lokalną. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testuje warunek dla każdej gałęzi i wykonuje działania w pierwszej gałęzi, dla którego warunek ma **wartość true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Reprezentuje gałąź elementu [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Umożliwia przepływowi pracy Wywoływanie usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Umożliwia przepływowi pracy wywoływanie innego przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|[Nasłuchiwanie](http://go.microsoft.com/fwlink?LinkID=65037)|Działanie złożone, które zawiera tylko działania podrzędne [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania listening](http://go.microsoft.com/fwlink?LinkID=65078).|
|[Działaniu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Umożliwia zaplanowanie co najmniej dwóch podrzędnych gałęzi działania **SequenceActivity** do przetwarzania w tym samym czasie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działaniu ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|[Zasady zasad](http://go.microsoft.com/fwlink?LinkID=65019)|Służy do reprezentowania kolekcji reguł. Reguła składa się z warunków i wynikających z nich akcji. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Policy](http://go.microsoft.com/fwlink?LinkID=65004).|
|[Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Tworzy wiele wystąpień pojedynczego działania podrzędnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Replikator](http://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Zapewnia prosty sposób łączenia wielu działań w celu wykonywania sekwencyjnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejście do nowego stanu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w przepływie pracy automatu Stanów. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Używane w działaniu [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) jako kontener dla działań podrzędnych, które są wykonywane przy opuszczaniu działania **działanie StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Używane w działaniu [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) jako kontener dla działań podrzędnych, które są wykonywane podczas wprowadzania działania **działanie StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|[Działanie SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Wstrzymuje działanie przepływu pracy w celu umożliwienia interwencji w przypadku niektórych warunków błędu, które wymagają szczególnej uwagi. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania zawieszania](http://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Wykonuje zawarte działania sekwencyjnie w zsynchronizowanej domenie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|[Zakończenie działania](http://go.microsoft.com/fwlink?LinkID=65058)|Umożliwia natychmiastowe zakończenie operacji przepływu pracy w przypadku warunku błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Terminate](http://go.microsoft.com/fwlink?LinkID=65086).|
|[Throw](http://go.microsoft.com/fwlink?LinkID=65059)|Umożliwia przechwytywanie wyjątków firmy zgłaszanych w ramach metadanych procesu dla przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania throw](http://go.microsoft.com/fwlink?LinkID=65087).|
|[Działania TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Zapewnia platformę dla transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Używanie działania TransactionScopes](http://go.microsoft.com/fwlink?LinkID=65088).|
|[Działanie WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Umożliwia modelowanie wystąpienia błędu usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|[Wykonan](http://go.microsoft.com/fwlink?LinkID=65047)|Odbiera dane z usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|[Działanie WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Odpowiada na żądanie usługi sieci Web wysłane do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|[While](http://go.microsoft.com/fwlink?LinkID=65049)|Umożliwia pętlę przepływu pracy do momentu spełnienia warunku. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania while](http://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] sposób tworzenia działań niestandardowych, zobacz [opracowywanie działań niestandardowych](http://go.microsoft.com/fwlink?LinkID=65023) i [Używanie starszej wersji projektanta działań](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>W tej sekcji
 [Widoki działań (starsza wersja)](../workflow-designer/activity-views-legacy.md) Opisuje różne widoki projektu działań.

 [Instrukcje: dodawanie działań do przybornika (starsza wersja)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Pokazuje, jak dodać działania do przybornika.

 [Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Przedstawia kroki tworzenia warunku reguły deklaratywnej.

 [Instrukcje: Tworzenie zestawu reguł zasad zabezpieczeń (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Przedstawia kroki tworzenia zestawu reguł zasad.

 [Instrukcje: Implementowanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Przedstawia kroki implementowania operacji [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu.

 [Instrukcje: wywoływanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Pokazuje procedurę wywoływania [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu.

## <a name="see-also"></a>Zobacz też
 [Działania Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005) [tworzenia przepływów](http://go.microsoft.com/fwlink?LinkID=65010) pracy [opracowywania działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65023)