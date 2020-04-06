---
title: IDebugStackFrame2::Właściwości wyliczenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719899"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Tworzy wyliczyć dla właściwości skojarzonych z ramką stosu, takich jak zmienne lokalne.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFieldSpec`\
[w] Kombinacja flag z wyliczenia [DEBUGPROP_INFO_FLAGS,](../../../extensibility/debugger/reference/debugprop-info-flags.md) która określa, które pola w wyliczonych [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur mają być wypełnione.

`nRadix`\
[w] Radix do wykorzystania w formatowaniu wszelkich informacji liczbowych.

`refiid`\
[w] Identyfikator GUID filtru służącego do wybierania [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur mają być wyliczone, takich jak `guidFilterLocals`.

`dwTimeout`\
[w] Maksymalny czas ( w milisekundach) oczekiwania przed zwróceniem tej metody. Służy `INFINITE` do oczekiwania przez czas nieokreślony.

`pcelt`\
[na zewnątrz] Zwraca liczbę wyliczonych właściwości. Jest to taka sama jak wywołanie [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) metody.

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugPropertyInfo2 zawierający](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) listę żądanych właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ponieważ ta metoda umożliwia wszystkie wybrane właściwości, które mają być pobierane za pomocą jednego wywołania, jest szybszy niż sekwencyjnie wywołanie [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) i [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
