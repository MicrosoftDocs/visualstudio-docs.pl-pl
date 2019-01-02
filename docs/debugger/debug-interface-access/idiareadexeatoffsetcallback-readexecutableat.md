---
title: Idiareadexeatoffsetcallback::readexecutableat — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d75529a2baebc6a5f488122106f47e512a4b9ac0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962159"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Odczytuje określoną liczbę bajtów, rozpoczynając od określonego przesunięcia przy użyciu pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 fileOffset  
 [in] Przesunięcie w pliku wykonywalnym ma rozpocząć się odczyt.  
  
 cbData  
 [in] Liczba bajtów do odczytania.  
  
 pcbData  
 [out] Zwraca liczbę odczytanych bajtów.  
  
 dane]  
 [out w] Tablica, która jest wypełniane bajtów odczytanych z pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez kod pomocy technicznej DIA załadować bajtów danych z pliku wykonywalnego przy użyciu przesunięcie bezwzględnej. Ta metoda jest wywoływana wspierających [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)