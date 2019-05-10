---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a02eb9048c0e9338e6300fc63666af4db535b3ac
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775714"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
```cpp#  
  
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
