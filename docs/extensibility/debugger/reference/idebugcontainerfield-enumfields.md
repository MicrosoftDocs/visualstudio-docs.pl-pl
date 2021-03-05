---
description: Tworzy moduł wyliczający dla pól kontenera.
title: 'IDebugContainerField:: EnumFields — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ec12cd97318fc41b97c5a7701dff2346524101
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143171"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Tworzy moduł wyliczający dla pól kontenera.

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
podczas Kombinacja [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) stałych, które wybierają pola do wyliczenia. Rodzaje pól mogą opisywać typy magazynów, takie jak Klasa lub pierwotne, lub określone informacje, takie jak lokalny, parametr lub wskaźnik "This".

`dwModifiersFilter`\
podczas Kombinacja [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) stałych, które wybierają pola do wyliczenia. Modyfikatory pola mogą być uprawnieniami dostępu, takimi jak publiczne lub prywatne, lub informacjami o magazynie, takimi jak wirtualne, statyczne lub końcowe.

`pszNameFilter`\
podczas Nazwa pola do wyliczenia. Może to być wartość null, jeśli wszystkie pola mają być zwracane.

`nameMatch`\
podczas Wartość z wyliczenia [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) , która kontroluje, czy w wyszukiwaniu jest rozróżniana wielkość liter.

`ppEnum`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę pól. Zwraca wartość null, jeśli nie ma żadnych pól.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub S_FALSE, jeśli nie ma żadnych pól. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `dwKindFilter`Parametry, `dwModifiersFilter` i `pszNameFilter` można łączyć, na przykład, aby wybrać wszystkie publiczne metody wirtualne o nazwie "nomethod".

## <a name="see-also"></a>Zobacz też
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
