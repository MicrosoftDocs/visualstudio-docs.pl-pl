---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98887e684d9bf2cbe282b7d9c4670fd18a355bd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864538"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Umożliwia aplikacji klienckiej dostarczanie bajtów pliku wykonywalnego określonego przez względny adres wirtualny.

## <a name="syntax"></a>Składnia

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtRVACallback` .

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

 DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)