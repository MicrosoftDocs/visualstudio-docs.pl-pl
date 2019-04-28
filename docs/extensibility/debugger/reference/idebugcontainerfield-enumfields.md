---
title: IDebugContainerField::EnumFields | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d770922203b92a533650a7eadf754effa3f24c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922336"
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

#### <a name="parameters"></a>Parametry
 `dwKindFilter`

 [in] Kombinacji [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) stałych, które wybierz pola, które mają zostać wyliczone. Typy pól można opisać typów magazynu, takich jak klasy lub pierwotnych lub określonych informacji, takich jak lokalne, parametr lub wskaźnika "this".

 `dwModifiersFilter`

 [in] Kombinacji [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) stałych, które wybierz pola, które mają zostać wyliczone. Modyfikatory pola może być uprawnienia dostępu, takie jak publiczny lub prywatny lub informacje dotyczące magazynu, takie jak wirtualne, statyczne lub końcowe.

 `pszNameFilter`

 [in] Nazwa pola do wyliczenia. Może to być wartość null, jeśli wszystkie pola, które mają zostać zwrócone.

 `nameMatch`

 [in] Wartość z zakresu od [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) wyliczenie, które określa, czy wyszukiwanie jest uwzględniana wielkość liter, czy nie.

 `ppEnum`

 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę pól. Zwraca wartość null, jeśli nie ma żadnych pól.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub S_FALSE, jeśli nie ma żadnych pól. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `dwKindFilter`, `dwModifiersFilter`, I `pszNameFilter` parametrów można łączyć, na przykład, aby wybrać wszystkie publiczne metody wirtualnej o nazwie "MyMethod".

## <a name="see-also"></a>Zobacz też
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)