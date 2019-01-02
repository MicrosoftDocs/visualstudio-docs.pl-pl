---
title: Idiaaddressmap::put_imagealign — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0188a0faa4f9fe7a711cbdfd7c006e7e423713fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879734"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Ustawia wyrównanie obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Nowa wartość wyrównania obrazu pliku wykonywalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obrazy (załadowanych plików wykonywalnych) są wyrównane na granicach pamięci określonej. Wyrównanie ten ma wpływ przez bieżący architektury systemu i opcje czasu kompilacji i łącza. Wyrównanie obrazu jest zawsze bajtowych granic. Prawidłowe są następujące wartości wyrównanie obrazu: 1, 2, 4, 8, 16, 32 i 64-bajtowych granicach.  
  
 Można pobrać bieżącego wyrównanie obrazu z wywołaniem [idiaaddressmap::get_imagealign —](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) metody.  
  
> [!NOTE]
>  Obraz, który jest już załadowany przez czas, który można wywołać tej metody. `put_imageAlign` Metoda jest zwykle używana, gdy obraz, który został przeniesiony lub zmienić, a nowe wyrównanie jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)