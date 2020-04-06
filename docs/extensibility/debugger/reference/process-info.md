---
title: PROCESS_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713883"
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
 Kombinacja flag z wyliczenia [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) określająca, które pola są wypełniane.

 `bstrFileName`\
 Pełna nazwa ścieżki procesu. Odpowiednik wywoływania [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody `GN_FILENAME`z parametrem .

 `bstrBaseName`\
 Nazwa pliku i rozszerzenie procesu. Odpowiednik wywoływania `IDebugProcess2::Getname` metody z `GN_BASENAME`parametrem .

 `bstrTitle`\
 Tytuł procesu, jeśli istnieje. Odpowiednik wywoływania `IDebugProcess2::Getname` metody z `GN_TITLE`parametrem .

 `ProcessId`\
 Struktura [AD_PROCESS_ID,](../../../extensibility/debugger/reference/ad-process-id.md) która identyfikuje proces. Odpowiednik wywoływania [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) metody.

 `dwSessionId`\
 Identyfikator sesji debugowania, w których jest uruchomiony ten proces.

 `bstrAttachedSessionName`\
 Załączona nazwa sesji. Odpowiednik wywoływania [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metody.

 `CreationTime`\
 Czas utworzenia procesu.

 `Flags`\
 Kombinacja flag z wyliczenia [PROCESS_INFO_FLAGS,](../../../extensibility/debugger/reference/process-info-flags.md) które określają właściwości procesu.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywana do [Metody GetInfo,](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) gdzie jest wypełniona.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
