---
title: IEnumDebugPortSuppliers2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715935"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Ten interfejs wylicza dostawców portów.

## <a name="syntax"></a>Składnia

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs do reprezentowania listy dostawców portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Zadzwoń [do EnumPortSuppliers,](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) aby uzyskać listę dostawców portów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugPortSuppliers2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Pobiera określoną liczbę dostawców portów w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Pomija określoną liczbę dostawców portów w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Pobiera liczbę dostawców portów w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania zazwyczaj nie trzeba uzyskać tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
