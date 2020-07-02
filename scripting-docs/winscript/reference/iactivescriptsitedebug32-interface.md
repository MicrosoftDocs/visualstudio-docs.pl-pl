---
title: Interfejs IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835267"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32, interfejs
Hosty inteligentne implementują `IActiveScriptSiteDebug32` interfejs do zarządzania dokumentami i uczestniczenia w debugowaniu. `IActiveScriptSite`Obiekt zazwyczaj zapewnia implementację `IActiveScriptSiteDebug32` interfejsu. Jeśli to zrobisz, wywołaj `IActiveScriptSite::QueryInterface` metodę, aby uzyskać `IActiveScriptSiteDebug32` interfejs.  
  
 Oprócz metod dziedziczonych z `IUnknown` , `IActiveScriptSiteDebug32` Interfejs udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Zwraca obiekt aplikacji debugowania skojarzony z tą lokacją skryptu.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Używane przez Aparat języka do delegowania `IDebugCodeContext::GetSourceContext` .|