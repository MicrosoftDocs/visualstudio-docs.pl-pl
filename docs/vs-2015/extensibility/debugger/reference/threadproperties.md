---
title: THREADPROPERTIES | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
 Kombinacja flag z wyliczenia [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , opisująca, które pola w tej strukturze są prawidłowe.  
  
 dwThreadId  
 Identyfikator wątku.  
  
 dwSuspendCount  
 Liczba wstrzymań wątku.  
  
 dwThreadState  
 Wartość z wyliczenia [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) wskazująca stan wątku operacyjnego.  
  
 bstrPriority  
 Ciąg określający priorytet wątku; na przykład "powyżej normalnego", "normalny" lub "czas krytyczne".  
  
 bstName  
 Nazwa wątku.  
  
 bstrLocation  
 Lokalizacja wątku (zazwyczaj ramka najwyższego stosu), zwykle wyrażona jako nazwa metody, w której wykonywanie jest aktualnie zatrzymane.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest wypełniana przez wywołanie metody [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Te informacje są zwykle używane do wypełniania okna **wątki** .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
