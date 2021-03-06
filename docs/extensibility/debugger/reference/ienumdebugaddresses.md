---
description: Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs IDebugAddress.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea9e4115c1664e1dcd05041f7ece056b5de01dae
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222643"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Ten interfejs reprezentuje kolekcję obiektów implementujących interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="syntax"></a>Składnia

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawcę symboli w celu udostępniania zestawów obiektów implementujących interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Należy zauważyć, że nie jest to standardowe wyliczenie COM z powodu obecności metody [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest zwracany przez [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) i [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Pobiera następny zestaw obiektów [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) z wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Pomija określoną liczbę wpisów.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Resetuje Wyliczenie do pierwszego wpisu.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Pobiera kopię bieżącego wyliczania.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zwykle używany przez aparat debugowania w celu określenia odpowiedniego adresu do przekazania do ewaluatora wyrażeń.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
