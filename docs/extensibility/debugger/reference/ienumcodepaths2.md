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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9758bacf6dc22ad65dc4d8db9b21d0f6728efaf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227089"
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
