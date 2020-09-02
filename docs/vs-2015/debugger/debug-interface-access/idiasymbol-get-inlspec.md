---
title: 'IDiaSymbol:: get_InlSpec | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 99a92f134390e5d3215b1609234e643b71d93d3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793661"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta funkcja Pobiera flagę wskazującą, czy funkcja została oznaczona jako wbudowana (przy użyciu jednego z [wbudowanych, __inline, \_ _forceinline](../../misc/inline-inline-forceinline.md) atrybutów).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_inlSpec(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca `TRUE` czy funkcja została oznaczona jako wbudowana; w przeciwnym razie zwraca `FALSE` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówki|dia2. h|  
|Wersja:|DIA SDK v 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [inline, __inline, \_ _forceinline](../../misc/inline-inline-forceinline.md)
