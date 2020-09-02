---
title: 'IDiaEnumDebugStreamData:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b80f71b2ca5d718f2de834389b4caab728e1f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197888"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera określony rekord.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 index  
 podczas Indeks rekordu do pobrania. Indeks znajduje się w zakresie od 0 do `count` -1, gdzie `count` jest zwracany przez [IDiaEnumDebugStreamData:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).  
  
 cbData  
 podczas Rozmiar buforu danych w bajtach.  
  
 pcbData  
 określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` jest `NULL` , `pcbData` zawiera łączną liczbę bajtów danych dostępnych w określonym rekordzie.  
  
 dane []  
 określoną Bufor, który jest wypełniony przy użyciu danych rekordu strumienia debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` dla nieprawidłowych parametrów i jeśli `index` parametr znajduje się poza zakresem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData:: Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)
