---
title: IDebugMethodField::EnumStaticLocals | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 006f1975c18aa7464531654d9b71fd857953afc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324244"
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

## <a name="parameters"></a>Parametry
`ppLocals`\
[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę statyczne zmienne lokalne. Zwraca wartość null, jeśli nie ma żadnych statycznych zmiennych lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych statycznych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący różnego rodzaju statyczne zmienne lokalne. Wywołaj [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody dla każdego obiektu, aby określić dokładnie rodzaj lokalny statyczne obiekt reprezentuje.

## <a name="see-also"></a>Zobacz także
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)