---
title: Idiadatasource::loaddataforexe — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13b852e917e55803fd37687ced86f819e0b591e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961044"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Zostanie otwarty i przygotowuje dane debugowania skojarzone z plikiem.exe/.dll.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pliku wykonywalnego  
 [in] Ścieżka do pliku .exe lub .dll.  
  
 searchPath  
 [in] Ścieżkę alternatywną, aby wyszukiwać dane debugowania.  
  
 pCallback  
 [in] `IUnknown` Interfejs dla obiektu, który obsługuje interfejs wywołania zwrotnego debugowania, takie jak [idialoadcallback —](../../debugger/debug-interface-access/idialoadcallback.md), [idialoadcallback2 —](../../debugger/debug-interface-access/idialoadcallback2.md), [idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), i/lub [idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfejsów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono niektóre możliwe kody błędów dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub plik ma nieprawidłowy format.|  
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku w formacie przestarzały.|  
|E_PDB_INVALID_SIG|Podpis nie odpowiada.|  
|E_PDB_INVALID_AGE|Okres ważności jest niezgodny.|  
|E_INVALIDARG|Nieprawidłowy parametr.|  
|WARTOŚĆ E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Nagłówek debugowania pliku.exe/.dll nazwy skojarzone debugowania lokalizacji danych.  
  
 Ta metoda odczytuje nagłówek debugowania i następnie wyszukuje i przygotowuje dane debugowania. Postęp wyszukiwania może opcjonalnie zgłaszane i kontrolowane za pośrednictwem wywołania zwrotne. Na przykład [idialoadcallback::notifydebugdir —](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) jest wywoływana po `IDiaDataSource::loadDataForExe` metoda umożliwia znalezienie i przetwarza katalog debugowania.  
  
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) i [idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfejsy umożliwiają aplikacji klienckiej zapewnić alternatywne metody do odczytywania danych z pliku wykonywalnego pliku, gdy plik nie są dostępne bezpośrednio przy użyciu standardowych plikowych operacji We/Wy.  
  
 Aby załadować plik .pdb bez weryfikacji, użyj [idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.  
  
 Aby sprawdzić poprawność pliku .pdb względem określone kryteria, należy użyć [idiadatasource::loadandvalidatedatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Aby załadować plik .pdb bezpośrednio z pamięci, należy użyć [idiadatasource::loaddatafromistream —](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idialoadcallback —](../../debugger/debug-interface-access/idialoadcallback.md)   
 [Idialoadcallback2 —](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Idialoadcallback::notifydebugdir —](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Idiadatasource::loadandvalidatedatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)