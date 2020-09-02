---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 856d0111e65b51b798dfe44a324c58c4db5457fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192423"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera bajty kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 podczas Liczba bajtów reprezentujących rozmiar buforu danych.  
  
 `pcbData`  
 określoną Zwraca liczbę bajtów reprezentujących bajty zwrócone. Jeśli `data` jest `NULL` , `pcbData` to całkowita liczba dostępnych bajtów danych.  
  
 `data[]`  
 określoną Bufor, który ma zostać wypełniony przez bajty źródłowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
