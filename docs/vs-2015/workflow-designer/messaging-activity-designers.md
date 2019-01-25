---
title: Projektanci działań Messaging | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 250b213fc3bc54d67f55d41c5eb3aba7e3488cd4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780037"
---
# <a name="messaging-activity-designers"></a>Projektanci działań Messaging
Projektanci działań obsługi komunikatów są używane do tworzenia i konfigurowania działań dotyczących komunikatów, które wysyłania i odbierania [!INCLUDE[indigo1](../includes/indigo1-md.md)] wiadomości z poziomu [!INCLUDE[wf](../includes/wf-md.md)] aplikacji. [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] Wprowadza pięciu działań dotyczących komunikatów i [!INCLUDE[wfd1](../includes/wfd1-md.md)] zawiera dwa nowe projektantom szablonów, które umożliwiają zarządzanie komunikatów w przepływie pracy. Tematy zawarte w tej sekcji i wymienione w poniższej tabeli zawierają wskazówki dotyczące sposobu używania [!INCLUDE[wfd2](../includes/wfd2-md.md)] projektantów działań i szablonu.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Działania komunikatu|Opis|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia niejawne Zarządzanie wiadomości działania przy użyciu elementu podrzędnego <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie, które służy do inicjowania korelacji bez wysyłania i odbierania wiadomości.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Receive> działania, który odbiera wiadomości z usługi.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Tworzy parę wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania.|  
|[Send](../workflow-designer/send-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Send> działań, która wysyła komunikat do usługi.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Tworzy parę wstępnie skonfigurowane <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań w ramach <xref:System.Activities.Statements.Sequence> działania.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania, co umożliwia przepływ transakcji w przepływie pracy.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Dla innych typów Projektanci działań zobacz następujące tematy.  
  
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)  
  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)  
  
 [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)  
  
 [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)  
  
 [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)  
  
 [Transakcja](../workflow-designer/transaction-activity-designers.md)  
  
 [Kolekcja](../workflow-designer/collection-activity-designers.md)  
  
 [Obsługa błędów](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)