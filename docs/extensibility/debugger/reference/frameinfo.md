---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84e7329acb3cdbff5c2f84fbd035867791012b2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877755"
---
# <a name="frameinfo"></a>FRAMEINFO
W tym artykule opisano ramki stosu.

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
m_dwValidFields A kombinacja flag z [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) wyliczenia, która określa, które pola są wypełniane.

m_bstrFuncName nazwy funkcji skojarzone z ramki stosu.

m_bstrReturnType zwracany typ ramki stosu.

m_bstrArgs argumenty do funkcji skojarzonych z ramki stosu.

m_bstrLanguage język, w której funkcja jest zaimplementowana.

m_bstrModule Nazwa modułu skojarzone z ramki stosu.

m_addrMin adresu minimalne stosu fizycznych.

m_addrMAX adres maksymalnej stosu fizycznych.

m_pFrame [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt, który reprezentuje tej ramki stosu.

m_pFrame [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) obiekt, który reprezentuje moduł, który zawiera tej ramki stosu.

m_fHasDebugInfo niezerowa Koniunkcja (`TRUE`) Jeśli informacje o debugowaniu istnieje w podanej ramce.

m_fHasDebugInfo niezerowa Koniunkcja (`TRUE`) Jeśli ramka stosu jest skojarzony z kodem, który nie jest już prawidłowy.

m_fHasDebugInfo niezerowa Koniunkcja (`TRUE`), jeśli ramka stosu jest oznaczona przez Menedżer debugowania sesji (SDM).

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany do [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metodę, aby wypełnić. Ta struktura również znajduje się na liście, który jest zawarty w [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejs, który z kolei jest zwracany z wywołania [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
