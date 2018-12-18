---
title: Idiadatasource::loaddatafrompdb — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd4700ba658aec5dd2cd59858cc243a7d79a523
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752828"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zostanie otwarty i przygotowuje plik bazy danych (PDB) programu jako źródło danych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pdbPath  
 [in] Ścieżka do pliku .pdb.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub określić, że plik ma nieprawidłowy format.|  
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku w formacie przestarzały.|  
|E_INVALIDARG|Nieprawidłowy parametr.|  
|WARTOŚĆ E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ładuje dane debugowania bezpośrednio z pliku .pdb.  
  
 Aby sprawdzić poprawność pliku .pdb względem określone kryteria, należy użyć [idiadatasource::loadandvalidatedatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Aby uzyskać dostęp do proces ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
 Aby załadować plik .pdb bezpośrednio z pamięci, należy użyć [idiadatasource::loaddatafromistream —](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.  
  
## <a name="example"></a>Przykład  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loadandvalidatedatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)



