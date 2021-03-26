---
description: Ten interfejs reprezentuje listę ścieżek kodu.
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e8ff8b4532ab67a969c8270eeb83bdf715e0b1c0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091737"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Ten interfejs reprezentuje listę ścieżek kodu.

## <a name="syntax"></a>Składnia

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować listę ścieżek kodu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) , aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumCodePaths2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Pobiera określoną liczbę ścieżek kodu w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Pomija określoną liczbę ścieżek kodu w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Pobiera liczbę ścieżek kodu w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Ścieżka kodu reprezentuje punkt rozgałęzienia lub wywołanie funkcji w programie. Lista ścieżek kodu reprezentuje ścieżkę, w której wykonano wykonywanie kodu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
