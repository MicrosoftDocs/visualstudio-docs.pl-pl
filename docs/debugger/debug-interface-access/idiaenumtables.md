---
title: IDiaEnumTables | Microsoft Docs
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
ms.openlocfilehash: d505219468f802a3eff9df0ad766fd1a353d5166
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743704"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Wylicza różne tabele zawarte w źródle danych.

## <a name="syntax"></a>Składnia

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDiaEnumTables`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Pobiera wersję [interfejsu IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) tego modułu wyliczającego.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Pobiera liczbę tabel.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Pobiera tabelę przy użyciu indeksu lub nazwy.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Pobiera określoną liczbę tabel w sekwencji wyliczenia.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Pomija określoną liczbę tabel w sekwencji wyliczenia.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs, wywołując metodę [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak uzyskać interfejs `IDiaEnumTables` z sesji. Aby zapoznać się z bardziej kompletnym przykładem korzystania z tabel, zobacz Interfejs [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .

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
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80. dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
