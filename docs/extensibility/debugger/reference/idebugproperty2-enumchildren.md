---
title: IDebugProperty2::EnumChildren | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cfbce26a84254158f088e8744c14154aef7f61a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681390"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Pobiera listę właściwości elementy podrzędne.

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

#### <a name="parameters"></a>Parametry
 `dwFields`

 [in] Kombinacja flag z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) wyliczenia, która określa pola, które w wyliczany [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur, które mają być wypełnione.

 `dwRadix`

 [in] Określa podstawy, który ma być używany w formatowaniu wszelkie dane liczbowe.

 `guidFilter`

 [in] Identyfikator GUID filtra używanego z `dwAttribFilter` i `pszNameFilter` parametry, aby wybrać opcję `DEBUG_PROPERTY_INFO` elementy podrzędne są do wyliczenia. Na przykład `guidFilterLocals` filtry dla zmiennych lokalnych.

 `dwAttribFilter`

 [in] Kombinacja flag z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) wyliczenie, które określa, jakiego rodzaju obiektów do wyliczenia, na przykład `DBG_ATTRIB_METHOD` dla wszystkich metod, które mogą być elementami podrzędnymi tej właściwości. W połączeniu z `guidFilter` i `pszNameFilter` parametrów.

 `pszNameFilter`

 [in] Nazwa filtra używanego z `guidFilter` i `dwAttribFilter` parametry, aby wybrać opcję `DEBUG_PROPERTY_INFO` elementy podrzędne są do wyliczenia. Na przykład ustawienie tego parametru do filtrów "MyX" dla wszystkich elementów podrzędnych o nazwie "MyX."

 `dwTimeout`

 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

 `ppEnum`

 [out] Zwraca [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiekt, który zawiera listę właściwości podrzędnej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)