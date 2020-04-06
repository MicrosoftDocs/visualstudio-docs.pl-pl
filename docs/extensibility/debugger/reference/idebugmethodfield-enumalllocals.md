---
title: IDebugMethodField::EnumAllLocals | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727334"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Tworzy wyliczyć dla wszystkich zmiennych lokalnych metody, w tym te generowane wewnętrznie przez kompilator.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[w] [Obiekt IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) reprezentujący adres debugowania w ramach metody, wskazując określony zakres lub kontekst.

`ppLocals`\
[na zewnątrz] Zwraca obiekt [IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę wszystkich mieszkańców w określonym zakresie; w przeciwnym razie zwraca wartość null wskazującą brak lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma mieszkańców. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyliczano tylko zmienne zdefiniowane w bloku zawierającym podany adres debugowania. Ta metoda obejmuje wszelkie lokalnych generowanych przez kompilator. Jeśli wszystko, co jest potrzebne są lokalni mieszkańcy jawnie zdefiniowane w źródle, wywołać [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) metody.

 Metoda może zawierać wiele kontekstów zakresu lub bloków.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
