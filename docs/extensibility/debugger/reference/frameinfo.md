---
title: FRAMEINFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736786"
---
# <a name="frameinfo"></a>FRAMEINFO
W tym artykule opisano ramkę stosu.

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
Kombinacja flag z wyliczenia [FRAMEINFO_FLAGS,](../../../extensibility/debugger/reference/frameinfo-flags.md) która określa, które pola są wypełniane.

`m_bstrFuncName`\
Nazwa funkcji skojarzona z ramką stosu.

`m_bstrReturnType`\
Typ zwracany skojarzony z ramką stosu.

`m_bstrArgs`\
Argumenty funkcji skojarzonej z ramką stosu.

`m_bstrLanguage`\
Język, w którym funkcja jest zaimplementowana.

`m_bstrModule`\
Nazwa modułu skojarzona z ramką stosu.

`m_addrMin`\
Minimalny adres stosu fizycznego.

`m_addrMAX`\
Maksymalny adres stosu fizycznego.

`m_pFrame`\
[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt, który reprezentuje tę ramkę stosu.

`m_pModule`\
[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) obiekt, który reprezentuje moduł, który zawiera tę ramkę stosu.

`m_fHasDebugInfo`\
Non-zero`TRUE`( ), jeśli informacje debugowania istnieją w danej ramce.

`m_fStaleCode`\
Non-zero`TRUE`( ), jeśli ramka stosu jest skojarzona z kodem, który nie jest już prawidłowy.

`m_fAnnotatedFrame`\
Non-zero`TRUE`( ), jeśli ramka stosu jest opisywana przez menedżera debugowania sesji (SDM).

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywana do [Metody GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) do wypełnienia. Ta struktura jest również zawarta na liście, która jest zawarta w interfejsie [IEnumDebugFrameInfo2,](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) który z kolei jest zwracany z wywołania do [Metody EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
