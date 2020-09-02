---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153616"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa sposób interpretacji identyfikatora procesu w strukturze [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Identyfikator procesu to identyfikator systemowy. Użyj `ProcessId.dwProcessId` pola struktury [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
 AD_PROCESS_ID_GUID  
 Identyfikator procesu jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pola `AD_PROCESS_ID` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Używane dla `ProcessIdType` elementu członkowskiego struktury [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) do identyfikowania typu identyfikatora procesu, który jest zawarty w strukturze. Określa sposób interpretacji `ProcessId` Unii w strukturze.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
