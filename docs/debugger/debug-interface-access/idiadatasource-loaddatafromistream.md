---
title: 'IDiaDataSource:: loadDataFromIStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2bcf657b4404ed72059351175d124a9c07abb46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744952"
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

podczas Obiekt <xref:IStream> reprezentujący strumień danych do użycia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku z przestarzałym formatem.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia uzyskanie danych debugowania dla pliku wykonywalnego z pamięci za pośrednictwem obiektu <xref:IStream>.

 Aby załadować plik. pdb bez sprawdzania poprawności, użyj metody [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

 Aby sprawdzić poprawność pliku. pdb względem określonych kryteriów, użyj metody [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

 Aby uzyskać dostęp do procesu ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)