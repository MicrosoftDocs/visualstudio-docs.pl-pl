---
title: Idiareadexeatrvacallback::readexecutableatrva — | Dokumentacja firmy Microsoft
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
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a94993260c7614b56d5b357c26793be7d1775e37
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750307"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Odczytuje określoną liczbę bajtów, zaczynając od określonego względny adres wirtualny (RVA) z pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `relativeVirtualAddress`  
 [in] RVA w pliku wykonywalnym ma rozpocząć się odczyt.  
  
 `cbData`  
 [in] Liczba bajtów do odczytania.  
  
 `pcbData`  
 [out] Zwraca liczbę odczytanych bajtów.  
  
 `data[]`  
 [out w] Tablica, która jest wypełniane bajtów odczytanych z pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez kod pomocy technicznej DIA załadować bajtów danych z pliku wykonywalnego przy użyciu względny adres wirtualny. Ta metoda jest wywoływana wspierających [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



