---
title: IDebugContainerField::EnumFields | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733224"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Tworzy wyliczenie dla pól kontenera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwKindFilter`\
[w] Kombinacja [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) stałych, które wybierają pola, które mają być wyliczone. Rodzaje pól można opisać typy magazynu, takie jak klasa lub prymitywne lub określonych informacji, takich jak wskaźnik lokalny, parametr lub "this".

`dwModifiersFilter`\
[w] Kombinacja [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) stałych, które wybierają pola, które mają być wyliczone. Modyfikatory pól mogą być uprawnienia dostępu, takie jak publiczne lub prywatne, lub informacje o magazynie, takie jak wirtualne, statyczne lub końcowe.

`pszNameFilter`\
[w] Nazwa pola, które ma być wyliczone. Może to być wartość null, jeśli wszystkie pola mają być zwracane.

`nameMatch`\
[w] Wartość z [wyliczenia NAME_MATCH,](../../../extensibility/debugger/reference/name-match.md) która kontroluje, czy wyszukiwanie jest rozróżniana wielkość liter, czy nie.

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę pól. Zwraca wartość null, jeśli nie ma żadnych pól.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub S_FALSE, jeśli nie ma żadnych pól. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `dwModifiersFilter` `pszNameFilter` , `dwKindFilter`i parametry mogą być łączone, na przykład, aby wybrać wszystkie publiczne metody wirtualne o nazwie "MyMethod".

## <a name="see-also"></a>Zobacz też
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
