---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aee44ff3acc1d7423e19de8fd64be0e46d8e372
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742804"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Umożliwia aplikacji klienckiej dostarczanie bajtów pliku wykonywalnego określonego przez względny adres wirtualny.

## <a name="syntax"></a>Składnia

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtRVACallback`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Odczytuje określoną liczbę bajtów, zaczynając od określonego względnego adresu wirtualnego (RVA) z pliku wykonywalnego.|

## <a name="remarks"></a>Uwagi
 Aplikacja kliencka implementuje ten interfejs, aby zapewnić bajty pliku wykonywalnego przy użyciu względnego adresu wirtualnego do pliku wykonywalnego. Aby użyć bezwzględnego przesunięcia pliku, zaimplementuj Interfejs [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ta metoda jest implementowana przez aplikację kliencką i przenoszona do metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) jako alternatywna metoda odczytu pliku.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)