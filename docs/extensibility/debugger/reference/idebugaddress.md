---
title: IDebugAddress | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653d2424d21a18e7053f66e0a74214ecc25d97da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317922"
---
# <a name="idebugaddress"></a>IDebugAddress
Ten interfejs reprezentuje adres elementu. Jest zwracany przez program obsługi symboli.

## <a name="syntax"></a>Składnia

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs reprezentujący adres obiektu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wiele metod w wielu interfejsach zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Pobiera [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury opisujący obiekt i jego lokalizacji.|

## <a name="remarks"></a>Uwagi
 Dostawca symboli zwraca ten interfejs reprezentujący obiekt i jego lokalizacji w ramach określonego zakresu (na przykład, funkcji, metody lub klasy). Ten interfejs jest zwracana z i przekazywane do różnych metod dostawca symboli i wyrażenie ewaluatora. Zazwyczaj dostawca symboli jest tylko jednostki, która wymaga nterpretowanie zawartości tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)