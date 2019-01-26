---
title: THREADPROPERTIES | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ad8b989b916e668fede0f8193c124d05785fd46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922668"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Opisuje właściwości wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwFields  
 Kombinacja flag z [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) wyliczenie, opisujące, które pola w tej strukturze są prawidłowe.  
  
 dwThreadId  
 Identyfikator wątku.  
  
 dwSuspendCount  
 Wątek wstrzymania count.  
  
 dwThreadState  
 Wartość z zakresu od [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Wyliczenie wskazujące stan wątku operacyjne.  
  
 bstrPriority  
 Ciąg określający priorytetu wątku; na przykład "Powyżej Normal", "Normal" lub "Czas krytyczne".  
  
 bstName  
 Nazwa wątku.  
  
 bstrLocation  
 Lokalizacja wątku (zazwyczaj ramki stosu najwyższego poziomu), zwykle wyrażona jako nazwa metody, w której obecnie wykonywanie zostało zatrzymane.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest wypełniane przez wywołanie [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody. Informacje, więc zwracana jest zwykle używana w wypełnianie **wątków** okna.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)