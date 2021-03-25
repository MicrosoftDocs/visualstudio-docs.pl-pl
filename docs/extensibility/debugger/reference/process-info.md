---
description: Zawiera informacje o procesie.
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6fe223d67b876dca1604b2617a33a888ec8180c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079647"
---
# <a name="process_info"></a>PROCESS_INFO
Zawiera informacje o procesie.

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
 `Fields`\
 Kombinacja flag z wyliczenia [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) , która określa, które pola są wypełniane.

 `bstrFileName`\
 Pełna nazwa ścieżki procesu. Równoważne wywołanie metody [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) z parametrem `GN_FILENAME` .

 `bstrBaseName`\
 Nazwa pliku i rozszerzenie procesu. Równoważne wywołanie `IDebugProcess2::Getname` metody z parametrem `GN_BASENAME` .

 `bstrTitle`\
 Tytuł procesu, jeśli taki istnieje. Równoważne wywołanie `IDebugProcess2::Getname` metody z parametrem `GN_TITLE` .

 `ProcessId`\
 Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , która identyfikuje proces. Równoważne z wywołaniem metody [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .

 `dwSessionId`\
 Identyfikator sesji debugowania, w której działa ten proces.

 `bstrAttachedSessionName`\
 Nazwa dołączonej sesji. Równoważne z wywołaniem metody [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .

 `CreationTime`\
 Godzina utworzenia procesu.

 `Flags`\
 Kombinacja flag z wyliczenia [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) , która określa właściwości procesu.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przenoszona do metody [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) , w której jest wypełniana.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
