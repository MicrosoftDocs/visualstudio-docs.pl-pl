---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df32012a100d36c8d288b6b988b9498ff4afd3b3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635738"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Umożliwia aplikacji klienta podać plik wykonywalny określony przez położenie pliku w bajtach.

## <a name="syntax"></a>Składnia

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtOffsetCallback`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Odczytuje określoną liczbę bajtów, rozpoczynając od określonego przesunięcia przy użyciu pliku wykonywalnego.|

## <a name="remarks"></a>Uwagi
 Aplikacja kliencka implementuje ten interfejs zapewnić bajtów wykonywalny wykorzystujący przesunięcie bezwzględna do pliku wykonywalnego. Aby użyć względny adres wirtualny, należy zaimplementować [idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ta metoda jest implementowana przez aplikację klienta i przekazywane do [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodę jako alternatywną metodą dla odczytu pliku.

## <a name="requirements"></a>Wymagania
 Nagłówek: Dia2.h

 Biblioteka: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)