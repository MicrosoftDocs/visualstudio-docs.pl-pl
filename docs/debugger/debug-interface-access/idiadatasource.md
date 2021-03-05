---
description: Inicjuje dostęp do źródła symboli debugowania.
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4932b3c787e1d17b5b32ea6a32bdd604692bda4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158247"
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicjuje dostęp do źródła symboli debugowania.

## <a name="syntax"></a>Składnia

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaDataSource` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Pobiera nazwę pliku dla ostatniego błędu ładowania.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Otwiera i przygotowuje plik bazy danych programu (. pdb) jako źródło danych debugowania.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Otwiera i weryfikuje, czy plik bazy danych programu (. pdb) pasuje do dostarczonych informacji o podpisie; przygotowuje plik. pdb jako źródło danych debugowania.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Otwiera i przygotowuje dane debugowania powiązane z plikiem exe/. dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Przygotowuje dane debugowania przechowywane w pliku bazy danych programu (. pdb) za pomocą strumienia danych znajdującego się w pamięci.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Otwiera sesję do wykonywania zapytań o symbole.|

## <a name="remarks"></a>Uwagi
Wywołanie jednej z metod ładowania `IDiaDataSource` interfejsu spowoduje otwarcie źródła symboli. Pomyślne wywołanie metody [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) zwraca interfejs [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , który obsługuje zapytania względem źródła danych. Jeśli metoda Load zwraca błąd związany z plikiem, wówczas wartość zwracana przez metodę [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) zawiera nazwę pliku skojarzoną z błędem.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Ten interfejs jest uzyskiwany przez wywołanie `CoCreateInstance` funkcji z identyfikatorem klasy `CLSID_DiaSource` i identyfikatorem interfejsu `IID_IDiaDataSource` . W przykładzie pokazano, jak zostanie uzyskany ten interfejs.

## <a name="example"></a>Przykład

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
