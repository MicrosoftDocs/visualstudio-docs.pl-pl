---
title: IEnumDebugAddresses | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717581"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="syntax"></a>Składnia

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawcę symboli, aby zapewnić zestawy obiektów, które implementują interfejs [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Należy zauważyć, że nie jest to standardowe wyliczenie COM ze względu na obecność [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) metody.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest zwracany przez [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) i [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Pobiera następny zestaw [obiektów IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) z wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Pomija określoną liczbę wpisów.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Resetuje wyliczenie do pierwszego wpisu.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Pobiera kopię bieżącego wyliczenia.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zazwyczaj używany przez aparat debugowania, aby określić odpowiedni adres do nadadawania oceniającemu wyrażenia.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
