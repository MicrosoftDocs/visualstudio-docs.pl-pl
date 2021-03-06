---
description: Wylicza atrybuty niestandardowe.
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8decd8d244ad4b55d2bba7381e247535faad9b22
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081077"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Wylicza atrybuty niestandardowe.

## <a name="syntax"></a>Składnia

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs, aby obsługiwał atrybuty niestandardowe (za pomocą interfejsu [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) ).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [EnumCustomAttributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugCustomAttributes` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Pobiera określoną liczbę atrybutów niestandardowych w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Pomija określoną liczbę atrybutów niestandardowych w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Pobiera liczbę atrybutów niestandardowych w module wyliczającym.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
