---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02338f46ace5da0d7769a6b27bc3500b797a9be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977658"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Pobiera bajtów sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Rozmiar buforu danych, w bajtach.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów sumy kontrolnej. Ten parametr nie może być `NULL`.  
  
 `data`  
 [out w] Buforu, który zostanie wypełniony kolorem bajtów sumy kontrolnej. Jeśli ten parametr jest `NULL`, następnie `pcbData` zwraca liczbę bajtów wymaganą.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ algorytmu sumy kontrolnej, który został użyty do wygenerowania sumy kontrolnej bajty, należy wywołać [idiasourcefile::get_checksumtype —](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) metody.  
  
 Suma kontrolna zwykle jest generowany z obrazu źródłowego pliku, więc zmiany w pliku źródłowym są odzwierciedlane na zmiany w bajtach sumy kontrolnej. Jeśli bajtów sumy kontrolnej nie są zgodne sumy kontrolnej wygenerowany na podstawie załadowanego obrazu pliku, a następnie plik należy rozważyć uszkodzony lub naruszony.  
  
 Typowe sumy kontrolne nigdy nie są więcej niż 32 bajty, rozmiar, ale nie należy zakładać, że jest maksymalny rozmiar sumy kontrolnej. Ustaw `data` parametr `NULL` do liczby bajtów wymaganej do pobierania sumy kontrolnej. Następnie przydziel bufor odpowiedni rozmiar i wywoływanie tej metody raz z bufor nowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)