---
title: Idiaenumtables — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20bd652437f0c1765686afc1d93a81bc9110236d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829122"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Wylicza różnych tabel znajdujących się w źródle danych.

## <a name="syntax"></a>Składnia

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDiaEnumTables`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Pobiera [interfejsu interfejs IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) wersję tego modułu wyliczającego.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Pobiera liczbę tabel.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Pobiera tabelę przy użyciu indeksu lub nazwę.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Pobiera określoną liczbę tabel w kolejności wyliczenia.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Pomija określoną liczbę tabel w kolejności wyliczenia.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskanie tego interfejsu, wywołując [idiasession::getenumtables —](../../debugger/debug-interface-access/idiasession-getenumtables.md) metody.

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak uzyskać `IDiaEnumTables` interfejsu z sesji. Aby uzyskać bardziej szczegółowy przykład użycia tabel, zobacz [idiatable —](../../debugger/debug-interface-access/idiatable.md) interfejsu.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
