---
description: Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs IDebugField.
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7534173fe927f1486e3f3c190ff2e427bb51bec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052921"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Składnia

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawcę symboli w celu udostępniania zestawów obiektów implementujących interfejs [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Należy zauważyć, że nie jest to standardowe wyliczenie COM z powodu obecności metody [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest zwracany przez [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) i [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Pobiera następny zestaw obiektów [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) z wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Pomija określoną liczbę wpisów.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Pobiera kopię bieżącego wyliczania.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
