---
title: Idiareadexeatrvacallback — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c86a0e995e3336bc217bcc9ad0e7ce28a6434478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832516"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Umożliwia aplikacji klienckiej umożliwiają określanie wartości bajtów plik wykonywalny określony przez względny adres wirtualny.

## <a name="syntax"></a>Składnia

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtRVACallback`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Odczytuje określoną liczbę bajtów, zaczynając od określonego względny adres wirtualny (RVA) z pliku wykonywalnego.|

## <a name="remarks"></a>Uwagi
 Aplikacja kliencka implementuje ten interfejs zapewnić bajtów wykonywalny wykorzystujący względny adres wirtualny do pliku wykonywalnego. Aby użyć przesunięcie bezwzględna do pliku, należy zaimplementować [idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ta metoda jest implementowana przez aplikację klienta i przekazywane do [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodę jako alternatywną metodą dla odczytu pliku.

## <a name="requirements"></a>Wymagania
 Nagłówek: Dia2.h

 Biblioteka: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)