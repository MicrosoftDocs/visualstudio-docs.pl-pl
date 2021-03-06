---
description: Ten interfejs wylicza dostawców portów.
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 893135291be3126055fa139dacaf3cc12141d8f4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224489"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Ten interfejs wylicza dostawców portów.

## <a name="syntax"></a>Składnia

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs, aby reprezentować listę dostawców portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , aby uzyskać listę dostawców portów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugPortSuppliers2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Pobiera określoną liczbę dostawców portów w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Pomija określoną liczbę dostawców portów w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Pobiera liczbę dostawców portów w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania zwykle nie musi uzyskać tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
