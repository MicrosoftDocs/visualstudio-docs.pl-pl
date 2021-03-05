---
description: Opisuje ramkę stosu.
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8830e3917198cda10d9e4e0fb8919b1b56e84e9e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144094"
---
# <a name="frameinfo"></a>FRAMEINFO
Opisuje ramkę stosu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Elementy członkowskie
`m_dwValidFields`\
Kombinacja flag z wyliczenia [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , która określa, które pola są wypełnione.

`m_bstrFuncName`\
Nazwa funkcji skojarzona z ramką stosu.

`m_bstrReturnType`\
Zwracany typ skojarzony z ramką stosu.

`m_bstrArgs`\
Argumenty funkcji skojarzonej z ramką stosu.

`m_bstrLanguage`\
Język, w którym funkcja jest zaimplementowana.

`m_bstrModule`\
Nazwa modułu skojarzona z ramką stosu.

`m_addrMin`\
Minimalny adres fizycznego stosu.

`m_addrMAX`\
Maksymalny adres fizycznego stosu.

`m_pFrame`\
Obiekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , który reprezentuje tę ramkę stosu.

`m_pModule`\
Obiekt [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , który reprezentuje moduł, który zawiera tę ramkę stosu.

`m_fHasDebugInfo`\
Wartość niezerowa ( `TRUE` ), jeśli w danej ramce istnieją informacje o debugowaniu.

`m_fStaleCode`\
Wartość niezerowa ( `TRUE` ), jeśli Ramka stosu jest skojarzona z kodem, który nie jest już prawidłowy.

`m_fAnnotatedFrame`\
Wartość niezerowa ( `TRUE` ), jeśli Ramka stosu ma adnotację z menedżerem debugowania sesji (SDM).

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona do metody [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) do wypełnienia. Ta struktura również znajduje się na liście zawartej w interfejsie [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , który z kolei jest zwracany przez wywołanie metody [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
