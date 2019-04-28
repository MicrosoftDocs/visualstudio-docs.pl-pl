---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a18d9a158e69fd18319f187274a2db7d00e24546
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913481"
---
# <a name="processinfo"></a>PROCESS_INFO
Zawiera informacje na temat procesu.

## <a name="syntax"></a>Składnia

```cpp
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
 Kombinacja flag z pól [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) wyliczenie określające, które pola są wypełnione.

 bstrFileName pełną nazwę ścieżki procesu. Równoważne z wywoływaniem [getname —](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody z parametrem `GN_FILENAME`.

 bstrBaseName nazwę pliku i rozszerzenie procesu. Równoważne z wywoływaniem `IDebugProcess2::Getname` metody z parametrem `GN_BASENAME`.

 bstrTitle tytuł proces, jeśli taka istnieje. Równoważne z wywoływaniem `IDebugProcess2::Getname` metody z parametrem `GN_TITLE`.

 ProcessId [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) strukturę, która identyfikuje proces. Równoważne z wywoływaniem [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) metody.

 dwSessionId identyfikator ten proces jest uruchomiony w sesji debugowania.

 Nazwa sesji dołączonych bstrAttachedSessionName. Równoważne z wywoływaniem [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metody.

 CreationTime czasu utworzenia procesu.

 Kombinacja flag z flag [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) wyliczenie określające właściwości procesu.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywany do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metody, gdzie jest wypełnione.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)