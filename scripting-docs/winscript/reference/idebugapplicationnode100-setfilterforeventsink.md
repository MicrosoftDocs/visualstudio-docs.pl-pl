---
title: IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 662c433134bc278f343381edcb4aedf383af6078
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446676"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Ustawia filtr na danym [interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementacji. Umożliwia ona debugery skrypt odfiltrować generowanych przez kompilator podrzędnych węzłów aplikacji tak, aby program PDM już nie będzie wysyłać zdarzenia, gdy są one tworzone lub usuwane. Domyślnie wszystkie węzły będą wysyłane.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) jest implementowany przez program PDM 10.0 lub nowszym. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Plik cookie filtru.  
  
 `filter`  
 Filtr.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationNode100, interfejs](../../winscript/reference/idebugapplicationnode100-interface.md)