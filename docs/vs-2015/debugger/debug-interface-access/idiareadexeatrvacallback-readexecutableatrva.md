---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187269"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Odczytuje określoną liczbę bajtów, zaczynając od określonego względnego adresu wirtualnego (RVA) z pliku wykonywalnego.  
  
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
 podczas Adres RVA w pliku wykonywalnym, aby rozpocząć odczytywanie.  
  
 `cbData`  
 podczas Liczba bajtów do odczytu.  
  
 `pcbData`  
 określoną Zwraca liczbę odczytanych bajtów.  
  
 `data[]`  
 [in. out] Tablica, która jest uzupełniona o Bajty odczytane z pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez kod obsługi DIA do ładowania bajtów danych z pliku wykonywalnego przy użyciu względnego adresu wirtualnego. Ta metoda jest wywoływana w ramach obsługi metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
