---
title: Idiaaddressmap::put_imagealign — | Dokumentacja firmy Microsoft
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
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c745d6b9df5f58b4aa2431a051e6fa583c73d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773707"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia wyrównanie obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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



