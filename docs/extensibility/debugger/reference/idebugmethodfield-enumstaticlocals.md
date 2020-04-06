---
title: IDebugMethodField::EnumStaticLocals | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727152"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Tworzy wyliczyć dla statycznych zmiennych lokalnych metody.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę statycznych lokalnych. Zwraca wartość null, jeśli nie ma żadnych statycznych lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych statycznych mieszkańców. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu reprezentujący różne typy statycznych lokalnych. Wywołanie [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody na każdy obiekt, aby określić dokładnie, jakiego rodzaju statyczne lokalne obiektu reprezentuje.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
