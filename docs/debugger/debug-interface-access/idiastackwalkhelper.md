---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40c2b58778b2a1073b31acc7007388d8e8fe222c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741302"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Ułatwia przechodzenie stosu przy użyciu pliku bazy danych debugowania programu (. pdb).

## <a name="syntax"></a>Składnia

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaStackWalkHelper`:

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Pobiera wartość rejestru.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Ustawia wartość rejestru.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Odczytuje blok danych z obrazu pliku wykonywalnego w pamięci.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Przeszukuje określoną ramkę stosu dla najbliższego adresu zwrotnego funkcji.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Przeszukuje określoną ramkę stosu dla adresu zwrotnego o określonym adresie stosu lub w jego prawie.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Pobiera ramkę stosu, która zawiera określony adres wirtualny.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Pobiera symbol, który zawiera określony adres wirtualny. **Uwaga:**  Symbol musi mieć typ `SymTagFunctionType` (wartość z wyliczenia [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Zwraca blok danych PDATA skojarzony z określonym adresem wirtualnym.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Pobiera początkowy adres wirtualny pliku wykonywalnego, pod adresem wirtualnym znajdującym się w miejscu pliku wykonywalnego.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest wywoływany przez kod DIA, aby uzyskać informacje na temat pliku wykonywalnego w celu skonstruowania listy ramek stosu podczas wykonywania programu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aplikacja kliencka implementuje ten interfejs, aby obsługiwać przechodzenie przez stos podczas wykonywania programu. Wystąpienie tego interfejsu jest przesyłane do metod [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) lub [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)