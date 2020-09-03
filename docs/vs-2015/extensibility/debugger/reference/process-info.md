---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205018"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zawiera informacje o procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Pola  
 Kombinacja flag z wyliczenia [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) , która określa, które pola są wypełniane.  
  
 bstrFileName  
 Pełna nazwa ścieżki procesu. Równoważne wywołanie metody [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) z parametrem `GN_FILENAME` .  
  
 bstrBaseName  
 Nazwa pliku i rozszerzenie procesu. Równoważne wywołanie `IDebugProcess2::Getname` metody z parametrem `GN_BASENAME` .  
  
 bstrTitle  
 Tytuł procesu, jeśli taki istnieje. Równoważne wywołanie `IDebugProcess2::Getname` metody z parametrem `GN_TITLE` .  
  
 Identyfikator procesu  
 Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , która identyfikuje proces. Równoważne z wywołaniem metody [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .  
  
 dwSessionId  
 Identyfikator sesji debugowania, w której działa ten proces.  
  
 bstrAttachedSessionName  
 Nazwa dołączonej sesji. Równoważne z wywołaniem metody [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .  
  
 CreationTime  
 Godzina utworzenia procesu.  
  
 Flagi  
 Kombinacja flag z wyliczenia [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) , która określa właściwości procesu.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przenoszona do metody [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) , w której jest wypełniana.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName —](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
