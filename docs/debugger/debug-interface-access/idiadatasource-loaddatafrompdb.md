---
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744936"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Otwiera i przygotowuje plik bazy danych programu (. pdb) jako źródło danych debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametry
pdbPath

podczas Ścieżka do pliku. pdb.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub określono, że plik ma nieprawidłowy format.|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku z przestarzałym formatem.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
Ta metoda ładuje dane debugowania bezpośrednio z pliku. pdb.

Aby sprawdzić poprawność pliku. pdb względem określonych kryteriów, użyj metody [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Aby uzyskać dostęp do procesu ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Aby załadować plik. pdb bezpośrednio z pamięci, użyj metody [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Przykład

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
