---
title: PROVIDER_FIELDS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec381484a0628715f593dad10848f6e8f4206eee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55071023"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
Określa właściwości skojarzone z dostawcą programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 PFIELD_PROGRAM_NODES  
 `ProgramNodes` Pole jest prawidłowe.  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 `fIsDebuggerPresent` Pole jest prawidłowe.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane w `Fields` członkiem [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktury, aby wskazać, pola, które struktury jawnie zostały wypełnione.  
  
 Te wartości można łączyć przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)