---
title: IDebugMethodField::EnumStaticLocals | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fb50271801d895ca73dbbc915ff95320183d032
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872914"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Tworzy moduł wyliczający statyczne zmienne lokalne, metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

#### <a name="parameters"></a>Parametry
 `ppLocals`

 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę statyczne zmienne lokalne. Zwraca wartość null, jeśli nie ma żadnych statycznych zmiennych lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych statycznych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący różnego rodzaju statyczne zmienne lokalne. Wywołaj [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody dla każdego obiektu, aby określić dokładnie rodzaj lokalny statyczne obiekt reprezentuje.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)