---
title: Interfejs IDebugApplicationNode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be864fdb9468668633322066bbbcf11569e4eb3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58147907"
---
# <a name="idebugapplicationnode-interface"></a>Interfejs IDebugApplicationNode
`IDebugApplicationNode` Interfejs rozszerza funkcjonalność `IDebugDocumentProvider` interfejs, dostarczając kontekstu w drzewie projektu.  
  
 Oprócz metod odziedziczone `IDebugDocumentProvider`, `IDebugApplicationNode` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Wylicza węzły podrzędne węzła tej aplikacji.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Zwraca węzeł nadrzędny tego węzła aplikacji.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Ustawia dostawcę dokument ten węzeł aplikacji.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Powoduje, że ta aplikacja jest zwolnienie wszystkich odwołań, a następnie wprowadź nieaktywny.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Dodaje ten węzeł aplikacji do drzewa określonego projektu.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Usuwa ten węzeł aplikacji z drzewa projektu.|