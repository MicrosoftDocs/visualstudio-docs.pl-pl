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
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302954"
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji
[!INCLUDE[wf](../includes/wf-md.md)] zawiera domyślny zestaw działań, które zapewniają funkcjonalność przepływu sterowania, warunków, obsługi zdarzeń, zarządzania stanami i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy można korzystać z działań dostarczonych przez system [!INCLUDE[wfd1](../includes/wfd1-md.md)]lub można tworzyć własne działania niestandardowe.

 Poniższa tabela zawiera listę wstępnie ustawionych działań [!INCLUDE[wf2](../includes/wf2-md.md)] Framework. Wiele, ale nie wszystkie z tych działań, są reprezentowane przez projektantów działań, do których można uzyskać dostęp z **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść go na powierzchni projektowej.

|Działanie|Opis|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Używane z działaniem **HandleExternalEventActivity** dla komunikacji wejściowej i wyjściowej z usługą lokalną. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[Działania CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Używany do przechowywania logiki oczyszczania dla działania złożonego anulowane przed ukończeniem wszystkich elementów podrzędnych działania złożonego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działania CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[Elementu CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Umożliwia dodanie Visual Basic lub C# kodu do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania elementu CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|Kompensowana wersja [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|Kompensowana wersja elementów **TransactionScope**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[Działania CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Umożliwia wywoływanie kodu w celu cofnięcia lub zrekompensowania operacji już wykonywanych przez przepływ pracy w przypadku wystąpienia błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działania CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Otoka dla jednej lub większej liczby działań, które wykonują kompensację ukończonego działania TransactionScope, [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Wykonuje działania podrzędne na podstawie warunku, który ma zastosowanie do działania [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) , i na podstawie warunków, które są stosowane oddzielnie dla każdego elementu podrzędnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[Opóźnienie](https://go.microsoft.com/fwlink?LinkID=65028)|Umożliwia tworzenie opóźnień w przepływie pracy, które są oparte na interwale limitów czasu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Opóźnij](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Zawija jedno lub więcej działań, które są wykonywane po wystąpieniu określonego zdarzenia. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Udostępnia strukturę służącą do kojarzenia zdarzeń z działaniem. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Wykonuje swoje główne działanie podrzędne współbieżnie przy użyciu [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[Działanie FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Używane do obsługi wyjątku określonego typu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Reprezentuje działanie złożone, które ma uporządkowaną listę działań podrzędnych typu [działanie FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Używane w połączeniu z działaniem [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) dla komunikacji wejścia i wyjścia z usługą lokalną. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Testuje warunek dla każdej gałęzi i wykonuje działania w pierwszej gałęzi, dla którego warunek ma **wartość true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Reprezentuje gałąź elementu [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Umożliwia przepływowi pracy Wywoływanie usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Umożliwia przepływowi pracy wywoływanie innego przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[Nasłuchiwanie](https://go.microsoft.com/fwlink?LinkID=65037)|Działanie złożone, które zawiera tylko działania podrzędne [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania listening](https://go.microsoft.com/fwlink?LinkID=65078).|
|[Działaniu ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Umożliwia zaplanowanie co najmniej dwóch podrzędnych gałęzi działania **SequenceActivity** do przetwarzania w tym samym czasie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działaniu ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Służy do reprezentowania kolekcji reguł. Reguła składa się z warunków i wynikających z nich akcji. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Policy](https://go.microsoft.com/fwlink?LinkID=65004).|
|[Działanie ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Tworzy wiele wystąpień pojedynczego działania podrzędnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Replikator](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Zapewnia prosty sposób łączenia wielu działań w celu wykonywania sekwencyjnego. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Określa przejście do nowego stanu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[Działanie StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w przepływie pracy automatu Stanów. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Używane w działaniu [działanie StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) jako kontener dla działań podrzędnych, które są wykonywane przy opuszczaniu działania **działanie StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Używane w działaniu [działanie StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) jako kontener dla działań podrzędnych, które są wykonywane podczas wprowadzania działania **działanie StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[Działanie SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Wstrzymuje działanie przepływu pracy w celu umożliwienia interwencji w przypadku niektórych warunków błędu, które wymagają szczególnej uwagi. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania zawieszania](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Wykonuje zawarte działania sekwencyjnie w zsynchronizowanej domenie. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[Zakończenie działania](https://go.microsoft.com/fwlink?LinkID=65058)|Umożliwia natychmiastowe zakończenie operacji przepływu pracy w przypadku warunku błędu. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania Terminate](https://go.microsoft.com/fwlink?LinkID=65086).|
|[Throw](https://go.microsoft.com/fwlink?LinkID=65059)|Umożliwia przechwytywanie wyjątków firmy zgłaszanych w ramach metadanych procesu dla przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania throw](https://go.microsoft.com/fwlink?LinkID=65087).|
|[Działania TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Zapewnia platformę dla transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Używanie działania TransactionScopes](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Umożliwia modelowanie wystąpienia błędu usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania działanie WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[Wykonan](https://go.microsoft.com/fwlink?LinkID=65047)|Odbiera dane z usługi sieci Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[Działanie WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Odpowiada na żądanie usługi sieci Web wysłane do przepływu pracy. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Umożliwia pętlę przepływu pracy do momentu spełnienia warunku. [!INCLUDE[crdefault](../includes/crdefault-md.md)][przy użyciu działania while](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] sposób tworzenia działań niestandardowych, zobacz [opracowywanie działań niestandardowych](https://go.microsoft.com/fwlink?LinkID=65023) i [Używanie starszej wersji projektanta działań](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>W tej sekcji
 [Widoki działań (starsza wersja)](../workflow-designer/activity-views-legacy.md) Opisuje różne widoki projektu działań.

 [Instrukcje: dodawanie działań do przybornika (starsza wersja)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Pokazuje, jak dodać działania do przybornika.

 [Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Przedstawia kroki tworzenia warunku reguły deklaratywnej.

 [Instrukcje: Tworzenie zestawu reguł zasad zabezpieczeń (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Przedstawia kroki tworzenia zestawu reguł zasad.

 [Instrukcje: Implementowanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Przedstawia kroki implementowania operacji [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu.

 [Instrukcje: wywoływanie operacji kontraktu WCF (starsza wersja)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Pokazuje procedurę wywoływania [!INCLUDE[indigo2](../includes/indigo2-md.md)] kontraktu.

## <a name="see-also"></a>Zobacz też
 [Działania Windows Workflow Foundation](https://go.microsoft.com/fwlink?LinkID=65005) [tworzenia przepływów](https://go.microsoft.com/fwlink?LinkID=65010) pracy [opracowywania działań przepływu pracy](https://go.microsoft.com/fwlink?LinkID=65023)