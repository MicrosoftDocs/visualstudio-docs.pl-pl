---
description: Ten interfejs wylicza DEBUG_REFERENCE_INFO struktur.
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27917741d6110f2811b39587607b05cd0075f986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082806"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Ten interfejs wylicza [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur.

## <a name="syntax"></a>Składnia

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi odwołań do obiektów w pamięci. Ten interfejs musi być zaimplementowany tylko w przypadku, gdy odwołania są obsługiwane.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Program Visual Studio wywołuje [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) , aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugReferenceInfo2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Pobiera określoną liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Pomija określoną liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Pobiera liczbę struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Odwołanie jest zasadniczo typem i adresem, natomiast właściwość jest nazwą, typem i adresem. Odwołanie będzie utrwalane, o ile obiekt istnieje w pamięci. Aby uzyskać więcej informacji, zobacz [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
