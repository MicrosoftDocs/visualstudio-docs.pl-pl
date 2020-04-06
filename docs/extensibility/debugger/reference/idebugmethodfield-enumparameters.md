---
title: IDebugMethodField::EnumParameters | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727194"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Tworzy wyliczyć dla parametrów metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[na zewnątrz] Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę parametrów do metody; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych parametrów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych parametrów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący różne typy parametrów. Wywołanie [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody na każdy obiekt, aby określić dokładnie, jaki rodzaj parametru reprezentuje obiekt.

 Parametr zawiera zarówno jego nazwę zmiennej, jak i jej typ. Pierwszym parametrem metody klasy jest zazwyczaj wskaźnik "this".

 Jeśli potrzebne są tylko typy parametrów, należy wywołać [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
