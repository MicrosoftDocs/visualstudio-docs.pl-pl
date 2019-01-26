---
title: PENDING_BP_STATE_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db6f2b84c0d10ed6be171ad1c3055ca8f02fa5db
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958164"
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
Określa flagi stan oczekujący punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PBPSF_NONE  
 Symbol zastępczy.  
  
 PBPSF_VIRTUALIZED  
 Określa zwirtualizowanych oczekujących punktów przerwania, który ma zostać powiązany za każdym razem, gdy nowy kod jest ładowany.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `flags` członkiem [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)