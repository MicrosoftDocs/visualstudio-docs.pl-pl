---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 246cdc245d6b6828eee7cd60e1aa94c487b77905
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153546"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje rozwiązanie punktu przerwania błędu, w tym lokalizacji, programu i wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwFields`  
 Kombinacja wartości z wyliczenia [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) określająca, które pola tej struktury są wypełnione.  
  
 `bpResLocation`  
 Unia [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , która określa lokalizację rozpoznawania punktów przerwania.  
  
 `pProgram`  
 Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje aplikację, w której wystąpił błąd punktu przerwania.  
  
 `pThread`  
 Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek, w którym działa aplikacja, która wygenerowała błąd punktu przerwania.  
  
 `bstrMessage`  
 Ciąg zawierający ostrzeżenie lub komunikat o błędzie wynikający z tego rozwiązania błędu.  
  
 `dwType`  
 Wartość z wyliczenia [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) , która określa typ błędu punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z metody [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
