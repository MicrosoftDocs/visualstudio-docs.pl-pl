---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d49c912ae14154fc552c76fc011596f4f22166f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153559"
---
# <a name="bp_condition"></a>BP_CONDITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje warunki, w których uruchamiany jest punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `pThread`  
 Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje aktywny wątek dla aplikacji, która zawiera punkt przerwania.  
  
 `styleCondition`  
 Wartość z wyliczenia [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) opisująca styl tego warunku punktu przerwania.  
  
 `bstrContext`  
 Lokalizacja punktu przerwania.  
  
 `bstrCondition`  
 Warunek wyzwalania punktu przerwania.  
  
 `nRadix`  
 Podstawy do użycia w ocenie wszelkich informacji numerycznych.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim struktur [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 Ta struktura jest również przenoszona jako parametr do metod [setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) i [setcondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [Setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [Setcondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
