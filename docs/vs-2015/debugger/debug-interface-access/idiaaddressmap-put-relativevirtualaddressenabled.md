---
title: Idiaaddressmap::put_relativevirtualaddressenabled — | Dokumentacja firmy Microsoft
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
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696ce435ddae6fbca5cb9f4a6abbf08a3d0e7eab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800979"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pozwoli to klientowi włączyć lub wyłączyć Obliczanie i Użyj względnych adresów wirtualnych (RVA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Ustaw `TRUE` umożliwiające, lub `FALSE` można wyłączyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Adresy dla obiektów debugowania opisane przez interfejsy DIA i względem pliku wykonywalnego obrazu podstawowego, mogą być pobierane jako względnych adresów wirtualnych.  
  
 Użycie RVA jest włączona, gdy segmentów są wstępnie załadowane z pliku PDB. Aby uzyskać bieżący stan użytkowania RVA, należy wywołać [idiaaddressmap::get_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metody.  
  
 `put_relativeVirtualAddress` Można wywołać metody, aby włączyć RVA po pomyślnym wywołaniem [idiaaddressmap::set_imageheaders —](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda ustanowiła nowe nagłówki obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::get_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)



