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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658934"
---
# <a name="messaging-activity-designers"></a>Projektanci działań Messaging
Projektanci działań obsługi komunikatów służą do tworzenia i konfigurowania działań związanych z obsługą komunikatów, które wysyłają i odbierają [!INCLUDE[indigo1](../includes/indigo1-md.md)] wiadomości z poziomu aplikacji [!INCLUDE[wf](../includes/wf-md.md)]. W [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] wprowadzono pięć działań związanych z obsługą komunikatów, a [!INCLUDE[wfd1](../includes/wfd1-md.md)] oferuje dwóch nowych projektantów szablonów, które umożliwiają zarządzanie komunikatami w ramach przepływu pracy. Tematy zawarte w tej sekcji i wymienione w poniższej tabeli zawierają wskazówki dotyczące korzystania z [!INCLUDE[wfd2](../includes/wfd2-md.md)] działań i projektantów szablonów.

## <a name="in-this-section"></a>W tej sekcji

|Aktywność komunikatów|Opis|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Tworzy i konfiguruje działanie <xref:System.ServiceModel.Activities.CorrelationScope>, które zapewnia niejawne zarządzanie podrzędnymi działaniami związanymi z obsługą komunikatów z obiektem <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Tworzy i konfiguruje działanie <xref:System.ServiceModel.Activities.InitializeCorrelation>, które jest używane do inicjowania korelacji bez wysyłania lub otrzymywania wiadomości.|
|[Receive](../workflow-designer/receive-activity-designer.md)|Tworzy i konfiguruje działanie <xref:System.ServiceModel.Activities.Receive>, które odbiera komunikat z usługi.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Tworzy wstępnie skonfigurowaną parę działań <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> w ramach działania <xref:System.Activities.Statements.Sequence>.|
|[Send](../workflow-designer/send-activity-designer.md)|Tworzy i konfiguruje działanie <xref:System.ServiceModel.Activities.Send>, które wysyła komunikat do usługi.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Tworzy wstępnie skonfigurowaną parę działań <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> w ramach działania <xref:System.Activities.Statements.Sequence>.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Tworzy i konfiguruje działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope>, które umożliwia przepływ transakcji do przepływu pracy.|

## <a name="reference"></a>Tematy pomocy
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