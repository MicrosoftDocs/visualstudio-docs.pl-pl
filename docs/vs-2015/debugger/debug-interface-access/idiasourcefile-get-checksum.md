---
title: Idiasourcefile::get_checksum — | Dokumentacja firmy Microsoft
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
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efbbd3b7e77de6d1124e04132dbf55dbfffa8871
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783238"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera bajtów sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)



