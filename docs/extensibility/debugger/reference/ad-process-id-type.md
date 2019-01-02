---
title: AD_PROCESS_ID_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27791b555d2f18e1e0a338bbfb5893f9047fd4e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819603"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Określa, jak interpretować procesu o identyfikatorze w [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 AD_PROCESS_ID_SYSTEM  
 Identyfikator procesu jest identyfikator systemu. Użyj `ProcessId.dwProcessId` pole [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.  
  
 AD_PROCESS_ID_GUID  
 Identyfikator procesu jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pole `AD_PROCESS_ID` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `ProcessIdType` członkiem [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury w celu określenia typu Identyfikator procesu, który znajduje się w strukturze. Określa, jak interpretować `ProcessId` Unii w strukturze.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)