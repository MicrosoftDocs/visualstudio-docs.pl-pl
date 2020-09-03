---
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190739"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera sumę kontrolną b.  
  
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
 podczas Rozmiar buforu danych w bajtach.  
  
 `pcbData`  
 określoną Zwraca liczbę bajtów sum kontrolnych. Ten parametr nie może być `NULL` .  
  
 `data`  
 [in. out] Bufor wypełniony sumą kontrolną. Jeśli ten parametr ma `NULL` wartość, `pcbData` zwraca liczbę wymaganych bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ algorytmu sum kontrolnych, który został użyty do wygenerowania bajtów sumy kontrolnej, wywołaj metodę [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 Suma kontrolna jest zazwyczaj generowana na podstawie obrazu pliku źródłowego, więc zmiany w pliku źródłowym zostaną odzwierciedlone w zmianach w bajtach sum kontrolnych. Jeśli liczba bajtów sum kontrolnych nie jest zgodna z sumą kontrolną wygenerowaną na podstawie załadowanego obrazu pliku, plik powinien być uważany za uszkodzony lub naruszony.  
  
 Typowe sumy kontrolne nigdy nie przekraczają 32 bajtów, ale nie zakładają, że jest to maksymalny rozmiar sumy kontrolnej. Ustaw `data` parametr na `NULL` , aby uzyskać liczbę bajtów potrzebnych do pobrania sumy kontrolnej. Następnie przydziel bufor o odpowiednim rozmiarze i Wywołaj tę metodę jeszcze raz z nowym buforem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
