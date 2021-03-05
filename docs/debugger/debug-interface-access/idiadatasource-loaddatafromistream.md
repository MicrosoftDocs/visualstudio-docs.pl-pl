---
description: Przygotowuje dane debugowania przechowywane w pliku bazy danych programu (. pdb) za pomocą strumienia danych znajdującego się w pamięci.
title: 'IDiaDataSource:: loadDataFromIStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8f68c3e11b07ef4be2824b4795291dfbc793c945
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158268"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Przygotowuje dane debugowania przechowywane w pliku bazy danych programu (. pdb) za pomocą strumienia danych znajdującego się w pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parametry
 pIStream

podczas <xref:IStream> Obiekt reprezentujący strumień danych do użycia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku z przestarzałym formatem.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia uzyskanie danych debugowania dla pliku wykonywalnego z pamięci za pośrednictwem <xref:IStream> obiektu.

 Aby załadować plik. pdb bez sprawdzania poprawności, użyj metody [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

 Aby sprawdzić poprawność pliku. pdb względem określonych kryteriów, użyj metody [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

 Aby uzyskać dostęp do procesu ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
