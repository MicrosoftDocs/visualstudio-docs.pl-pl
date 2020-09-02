---
title: 'IDiaSymbol:: get_callingConvention | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: febbdd44935ee51136049157f7f04c0a10115267
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64797208"
---
# <a name="idiasymbolget_callingconvention"></a>IDiaSymbol::get_callingConvention
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca wskaźnik metody wywoływania Konwencji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_callingConvention (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca wartość z wyliczenia [CV_call_e](../../debugger/debug-interface-access/cv-call-e.md) , która określa konwencję wywoływania metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówki|dia2. h|  
|Wersja:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_call_e, wyliczenie](../../debugger/debug-interface-access/cv-call-e.md)
