---
title: THREADPROPERTIES | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204822"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje właściwości wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
