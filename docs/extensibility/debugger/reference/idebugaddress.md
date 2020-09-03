---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736593"
---
# <a name="idebugaddress"></a>IDebugAddress
Ten interfejs reprezentuje adres elementu. Jest zwracany przez procedurę obsługi symboli.

## <a name="syntax"></a>Składnia

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs, aby reprezentować adres obiektu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wiele metod w wielu interfejsach zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Pobiera strukturę [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) opisującą obiekt i jego lokalizację.|

## <a name="remarks"></a>Uwagi
 Dostawca symboli zwraca ten interfejs, aby reprezentować obiekt i jego lokalizację w ramach określonego zakresu (na przykład funkcja, metoda lub Klasa). Ten interfejs jest zwracany z i przeszedł do różnych metod dostawcy symboli i ewaluatora wyrażeń. Zwykle dostawca symboli jest jedyną jednostką, która musi interpretować zawartość tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
