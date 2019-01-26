---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b55dad4ba557e85291d572ef24b1ad12e08a3c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930683"
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicjuje dostęp do źródła symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaDataSource`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Pobiera nazwę pliku dla ostatniego błędu ładowania.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Zostanie otwarty i przygotowuje plik bazy danych (PDB) programu jako źródło danych debugowania.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Zostanie otwarty i sprawdza, czy plik bazy danych (PDB) programu odpowiada informacjami podpisu; przygotowuje plik .pdb jako źródło danych debugowania.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Zostanie otwarty i przygotowuje dane debugowania skojarzone z plikiem.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Przygotowuje dane debugowania przechowywane w pliku bazy danych (PDB) program dostępne za pośrednictwem strumień danych w pamięci.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Zostanie otwarta sesja zapytań symboli.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie jednej z metod obciążenia `IDiaDataSource` interfejsu otwiera źródło symboli. Pomyślne wywołanie [idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md) metoda zwraca [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu, który obsługuje badania źródła danych. Jeśli metoda load zwrócą błąd związany z plikami, a następnie [idiadatasource::get_lasterror —](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) metoda zwraca wartość zawiera nazwę pliku, skojarzony z błędem.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest można uzyskać przez wywołanie `CoCreateInstance` funkcji z identyfikatorem klasy `CLSID_DiaSource` i identyfikator interfejsu `IID_IDiaDataSource`. W przykładzie przedstawiono sposób uzyskiwania tego interfejsu.  
  
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
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)