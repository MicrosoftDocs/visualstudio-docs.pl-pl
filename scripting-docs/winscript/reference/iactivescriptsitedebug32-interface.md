---
title: IActiveScriptSiteDebug32 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345568"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Interface
Implementowanie hostów inteligentnych `IActiveScriptSiteDebug32` interfejsu, aby wykonać Zarządzanie dokumentami i do wzięcia udziału w debugowaniu. `IActiveScriptSite` Obiekt zwykle zawiera implementację `IActiveScriptSiteDebug32` interfejsu. Jeśli zostanie to zrobione, należy wywołać `IActiveScriptSite::QueryInterface` metodę, aby uzyskać `IActiveScriptSiteDebug32` interfejsu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IActiveScriptSiteDebug32` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Zwraca obiekt aplikacji debugowania, które są skojarzone z tą lokacją skryptu.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Używane przez aparat języka, aby delegować `IDebugCodeContext::GetSourceContext`.|