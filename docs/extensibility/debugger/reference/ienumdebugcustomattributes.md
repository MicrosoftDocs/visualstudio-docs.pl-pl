---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e706999595033ac76508eaa5e3b3f995839ceaea
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321557"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Wylicza atrybutów niestandardowych.

## <a name="syntax"></a>Składnia

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs do obsługi atrybuty niestandardowe (za pośrednictwem [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [Enumcustomattributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugCustomAttributes`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Pobiera określoną liczbę atrybutów niestandardowych, w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Pomija określoną liczbę atrybutów niestandardowych, w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Pobiera moduł wyliczający liczba atrybutów niestandardowych.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)