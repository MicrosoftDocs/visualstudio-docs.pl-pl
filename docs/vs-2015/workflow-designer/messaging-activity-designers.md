---
title: Projektanci działań obsługi komunikatów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658934"
---
# <a name="messaging-activity-designers"></a>Projektanci działań Messaging
Projektanci działań obsługi komunikatów służą do tworzenia i konfigurowania działań związanych z obsługą wiadomości, które wysyłają i odbierają [!INCLUDE[indigo1](../includes/indigo1-md.md)] wiadomości z [!INCLUDE[wf](../includes/wf-md.md)] aplikacji. W [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] programie wprowadzono pięć działań związanych z obsługą komunikatów i [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostępne są dwa nowe projektanci szablonów, które umożliwiają zarządzanie komunikatami w ramach przepływu pracy. Tematy zawarte w tej sekcji i wymienione w poniższej tabeli zawierają wskazówki dotyczące korzystania z [!INCLUDE[wfd2](../includes/wfd2-md.md)] projektantów działań i szablonów.

## <a name="in-this-section"></a>W tej sekcji

|Aktywność komunikatów|Opis|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które zapewnia niejawne zarządzanie podrzędnymi działaniami związanymi z obsługą komunikatów z <xref:System.ServiceModel.Activities.CorrelationHandle> obiektem.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.InitializeCorrelation> działanie, które jest używane do inicjowania korelacji bez wysyłania lub otrzymywania wiadomości.|
|[Odbieranie](../workflow-designer/receive-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Receive> działanie, które odbiera komunikat z usługi.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Tworzy wstępnie skonfigurowaną parę <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania w ramach <xref:System.Activities.Statements.Sequence> działania.|
|[Wysyłanie](../workflow-designer/send-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.Send> działanie, które wysyła komunikat do usługi.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Tworzy wstępnie skonfigurowaną parę <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania w ramach <xref:System.Activities.Statements.Sequence> działania.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Tworzy i konfiguruje <xref:System.ServiceModel.Activities.TransactedReceiveScope> działanie, które umożliwia przepływ transakcji do przepływu pracy.|

## <a name="reference"></a>Dokumentacja
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>Sekcje pokrewne
 W przypadku innych typów projektantów działań zapoznaj się z następującymi tematami.

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