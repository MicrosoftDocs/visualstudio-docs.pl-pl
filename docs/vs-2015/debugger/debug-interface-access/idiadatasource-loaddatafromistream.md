---
title: Idiadatasource::loaddatafromistream — | Dokumentacja firmy Microsoft
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
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8be3b85f77c5395a038e15925ca8654ea12ef60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817838"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przygotowuje dane debugowania przechowywane w pliku bazy danych (PDB) program dostępne za pośrednictwem strumień danych w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pIStream  
 [in] <xref:IStream> Obiekt reprezentujący strumień danych do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_FORMAT|Podjęto próbę uzyskania dostępu do pliku w formacie przestarzały.|  
|E_INVALIDARG|Invalidparameter.|  
|WARTOŚĆ E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia dane debugowania pliku wykonywalnego, które mają zostać uzyskane od ilości pamięci za pomocą <xref:IStream> obiektu.  
  
 Aby załadować plik .pdb bez weryfikacji, użyj [idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.  
  
 Aby sprawdzić poprawność pliku .pdb względem określone kryteria, należy użyć [idiadatasource::loadandvalidatedatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Aby uzyskać dostęp do proces ładowania danych (za pomocą mechanizmu wywołania zwrotnego), należy użyć [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)



