---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d80242ca516c5fa7f3ad297250e25c782664d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350382"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Ten interfejs reprezentuje kolekcję obiektów Implementowanie [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.

## <a name="syntax"></a>Składnia

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawcę symbol zapewnienie zestawów obiektów, które implementują [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu. Pamiętaj, że nie jest standardowy wyliczanie modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) metody.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest zwracany przez [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) i [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Ten interfejs implementuje są następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Pobiera następny zestaw [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektów z wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Pomija określoną liczbę pozycji.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Pobiera kopię bieżącego wyliczenia.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)