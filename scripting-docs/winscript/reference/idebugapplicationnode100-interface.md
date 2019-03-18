---
title: Interfejs IDebugApplicationNode100 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f380245422047142b3f06757f6c1057302dd5d26
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146048"
---
# <a name="idebugapplicationnode100-interface"></a>Interfejs IDebugApplicationNode100
`IDebugApplicationNode100` Interfejs rozszerza funkcjonalność [interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). Wystąpienie tego interfejsu można uzyskać za pomocą wywołania QueryInterface na implementację [interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Ten interfejs jest implementowany przez program PDM 10.0 lub nowszym. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationNode100` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Pobiera dokumenty tekstowe, ukryte przez określony filtr.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Ustawia filtr na danym [interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementacji. Umożliwia ona debugery skrypt odfiltrować generowanych przez kompilator podrzędnych węzłów aplikacji tak, aby program PDM już nie będzie wysyłać zdarzenia, gdy węzły są tworzone lub usuwane. Domyślnie wszystkie węzły będą wysyłane.|