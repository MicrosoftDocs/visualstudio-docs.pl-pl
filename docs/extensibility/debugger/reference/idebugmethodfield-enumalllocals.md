---
description: Tworzy moduł wyliczający dla wszystkich zmiennych lokalnych metody, włącznie z wygenerowanymi wewnętrznie przez kompilator.
title: 'IDebugMethodField:: EnumAllLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 021dd54157a46e35c0acbb7dd7315fe155304b6d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076696"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Tworzy moduł wyliczający dla wszystkich zmiennych lokalnych metody, włącznie z wygenerowanymi wewnętrznie przez kompilator.

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
podczas Obiekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) reprezentujący adres debugowania wewnątrz metody wskazujący określony zakres lub kontekst.

`ppLocals`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę wszystkich elementów lokalnych w określonym zakresie; w przeciwnym razie zwraca wartość null wskazującą brak wartości lokalnych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych ustawień lokalnych. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyliczane są tylko zmienne zdefiniowane w bloku, który zawiera dany adres debugowania. Ta metoda obejmuje wszystkie elementy lokalne generowane przez kompilator. Jeśli wszystkie elementy, które są wymagane, są lokalne jawnie zdefiniowane w źródle, wywołaj metodę [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .

 Metoda może zawierać wiele kontekstów lub bloków określania zakresu.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
