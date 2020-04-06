---
title: IDebugProperty2::WyliczeniaDzieci | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721511"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Pobiera listę korżenia obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[w] Kombinacja flag z wyliczenia [DEBUGPROP_INFO_FLAGS,](../../../extensibility/debugger/reference/debugprop-info-flags.md) która określa, które pola w wyliczonych [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur mają być wypełnione.

`dwRadix`\
[w] Określa radix, który ma być używany do formatowania dowolnych informacji liczbowych.

`guidFilter`\
[w] Identyfikator GUID filtru `dwAttribFilter` używanego z parametrami i `pszNameFilter` parametrami, aby wybrać elementy podrzędne, które `DEBUG_PROPERTY_INFO` mają być wyliczone. Na przykład `guidFilterLocals` filtry dla zmiennych lokalnych.

`dwAttribFilter`\
[w] Kombinacja flag z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) wyliczenia, która określa, jaki typ obiektów do wyliczenia, na przykład `DBG_ATTRIB_METHOD` dla wszystkich metod, które mogą być części podrzędnych tej właściwości. Używany w połączeniu `guidFilter` `pszNameFilter` z parametrami i.

`pszNameFilter`\
[w] Nazwa filtru używanego `guidFilter` z `dwAttribFilter` i parametrów, aby wybrać, które `DEBUG_PROPERTY_INFO` elementy podrzędne mają być wyliczone. Na przykład ustawienie tego parametru na filtry "MyX" dla wszystkich dziewiętnastych dzieci o nazwie "MyX".

`dwTimeout`\
[w] Określa maksymalny czas oczekiwania w milisekundach przed zwróceniem z tej metody. Służy `INFINITE` do oczekiwania przez czas nieokreślony.

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugPropertyInfo2 zawierający](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) listę właściwości podrzędnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
