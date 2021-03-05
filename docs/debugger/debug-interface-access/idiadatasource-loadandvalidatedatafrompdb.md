---
description: Otwiera i weryfikuje, czy plik bazy danych programu (. pdb) pasuje do dostarczonych informacji o podpisie i przygotowuje plik. pdb jako źródło danych debugowania.
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d55053271e38ee87533a11a8c5f6cd30d7e7333
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158289"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Otwiera i weryfikuje, czy plik bazy danych programu (. pdb) pasuje do dostarczonych informacji o podpisie i przygotowuje plik. pdb jako źródło danych debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Parametry
`pdbPath`

podczas Ścieżka do pliku. pdb.

`pcsig70`

podczas Podpis GUID, który ma zostać zweryfikowany względem sygnatury pliku. pdb. Tylko pliki. pdb w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i nowszych mają sygnatury GUID.

`sig`

podczas Podpis 32-bitowy, który ma zostać zweryfikowany względem sygnatury pliku. pdb.

`age`

podczas Wartość wieku do zweryfikowania. Wiek nie musi odpowiadać żadnej znanej wartości czasu, jest używany do określenia, czy plik. pdb nie jest zsynchronizowany z odpowiednim plikiem exe.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub plik ma nieprawidłowy format.|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku z przestarzałym formatem.|
|E_PDB_INVALID_SIG|Sygnatura nie jest zgodna.|
|E_PDB_INVALID_AGE|Wiek nie jest zgodny.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
Plik. pdb zawiera wartości sygnatur i wieku. Te wartości są replikowane w pliku exe lub dll, który pasuje do pliku. pdb. Przed przystąpieniem do przygotowywania źródła danych ta metoda sprawdza, czy nazwany plik. pdb jest zgodny z podanymi wartościami.

Aby załadować plik. pdb bez sprawdzania poprawności, użyj metody [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Aby uzyskać dostęp do procesu ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Aby załadować plik. pdb bezpośrednio z pamięci, użyj metody [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Przykład

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
