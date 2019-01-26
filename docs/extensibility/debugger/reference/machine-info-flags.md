---
title: MACHINE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO_FLAGS
helpviewer_keywords:
- MACHINE_INFO_FLAGS enumeration
ms.assetid: 1482095d-9a2e-4ef1-9e14-362c0b85194e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c3a444da9ea10eb560899a8ebce18ce7f72174c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937967"
---
# <a name="machineinfoflags"></a>MACHINE_INFO_FLAGS
Używane do opisywania na maszynie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
typedef DWORD MACHINE_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MCIFLAG_TERMINAL_SERVICES_AVAILABLE  
 Wskazuje, czy usługi terminalowe są dostępne.  
  
## <a name="remarks"></a>Uwagi  
 Używane jako `Flags` członkiem [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)