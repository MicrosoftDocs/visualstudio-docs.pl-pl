---
title: CANSTOP_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 409fecf26a33c77cb2e0dabaa52d789b4179451b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914867"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Używany do określenia, jeśli program zatrzymać wykonywanie po osiągnięciu określonego punktu w realizacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 CANSTOP_ENTRYPOINT  
 Określa punkt wejścia w danym programu.  
  
 CANSTOP_STEPIN  
 Określa, przechodzenie krok po kroku do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [getreason —](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby potwierdzić z sesji debugowania Manager (SDM), jeśli ma nic złego zatrzymać po osiągnięciu punktu wejścia programu, lub po przejściu do funkcji lub metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)