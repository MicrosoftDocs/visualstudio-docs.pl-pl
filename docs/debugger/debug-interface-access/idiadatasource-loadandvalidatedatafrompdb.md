---
title: Idiadatasource::loadandvalidatedatafrompdb — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5426e27d7b100c42cd571935b1634d6dbd6e990f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626144"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Zostanie otwarty i sprawdza, czy plik bazy danych (PDB) programu odpowiada informacjami podpisu i przygotowuje plik .pdb jako źródło danych debugowania.

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

[in] Ścieżka do pliku .pdb.

`pcsig70`

[in] Podpis identyfikator GUID do weryfikacji podpisu pliku .pdb. Pliki .pdb tylko [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i później mają podpisy identyfikatora GUID.

`sig`

[in] Podpis 32-bitowego do weryfikacji podpisu pliku .pdb.

`age`

[in] Wiek wartości w celu zweryfikowania. Wiek nie musi odpowiadać do każdej wartości czasu, jest on używany do określenia, czy plik .pdb jest zsynchronizowany z odpowiedniego pliku .exe.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub plik ma nieprawidłowy format.|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku w formacie przestarzały.|
|E_PDB_INVALID_SIG|Podpis nie odpowiada.|
|E_PDB_INVALID_AGE|Okres ważności jest niezgodny.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
Plik .pdb zawiera wartości zarówno podpis, jak i wieku. Te wartości są replikowane w pliku .exe lub .dll, który pasuje do pliku .pdb. Przed przygotowaniem źródła danych, ta metoda sprawdza, czy podpis i wiek pliku .pdb o nazwie odpowiadają podanych wartości.

Aby załadować plik .pdb bez weryfikacji, użyj [idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.

Aby uzyskać dostęp do proces ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.

Aby załadować plik .pdb bezpośrednio z pamięci, należy użyć [idiadatasource::loaddatafromistream —](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.

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

## <a name="see-also"></a>Zobacz też
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
