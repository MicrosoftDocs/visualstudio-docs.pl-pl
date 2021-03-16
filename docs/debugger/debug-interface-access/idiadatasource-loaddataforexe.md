---
description: Otwiera i przygotowuje dane debugowania powiązane z plikiem exe/. dll.
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 649efd5202d8b153b5fe5b4dbf9ba5052883f352
ms.sourcegitcommit: 66951f064d601b1d7a2253cb9b250380807e12db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483185"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Otwiera i przygotowuje dane debugowania powiązane z plikiem exe/. dll.

## <a name="syntax"></a>Składnia

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Parametry
plik

podczas Ścieżka do pliku exe lub dll.

searchPath

podczas Alternatywna ścieżka do wyszukiwania danych debugowania.

pCallback

podczas `IUnknown` Interfejs obiektu, który obsługuje interfejs wywołania zwrotnego debugowania, taki jak [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)i/lub [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono niektóre możliwe kody błędów dla tej metody.

|Wartość|Opis|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub plik ma nieprawidłowy format.|
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku z przestarzałym formatem.|
|E_PDB_INVALID_SIG|Sygnatura nie jest zgodna.|
|E_PDB_INVALID_AGE|Wiek nie jest zgodny.|
|E_INVALIDARG|Nieprawidłowy parametr.|
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|

## <a name="remarks"></a>Uwagi
Nagłówek debugowania pliku. exe/. dll nazywa skojarzoną lokalizację danych debugowania.

Jeśli ładujesz dane debugowania z serwera symboli, *symsrv.dll* musi znajdować się w tym samym katalogu, w którym zainstalowano aplikację lub *msdia140.dll* użytkownika, lub muszą one znajdować się w katalogu systemowym.

Ta metoda odczytuje nagłówek debugowania, a następnie wyszukuje i przygotowuje dane debugowania. Postęp wyszukiwania może, opcjonalnie, być raportowany i kontrolowany przez wywołania zwrotne. Na przykład, [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) jest wywoływana, gdy `IDiaDataSource::loadDataForExe` Metoda odnajdzie i przetwarza katalog debugowania.

Interfejsy [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) i [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) umożliwiają aplikacji klienckiej dostarczanie alternatywnych metod odczytywania danych z pliku wykonywalnego, gdy nie można uzyskać dostępu do pliku bezpośrednio za pośrednictwem standardowego we/wy pliku.

Aby załadować plik. pdb bez sprawdzania poprawności, użyj metody [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Aby sprawdzić poprawność pliku. pdb względem określonych kryteriów, użyj metody [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Aby załadować plik. pdb bezpośrednio z pamięci, użyj metody [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Przykład

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
