---
title: IDiaPropertyStorage::ReadBOOL | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794993"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Odczytuje `BOOL` wartości w zbiorze właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator właściwości do odczytu (`PROPID` jest zdefiniowany w WTypes.h jako `ULONG`).  
  
 `pValue`  
 [out] Zwraca wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` Jeśli właściwość nie jest typu `BOOL`.  
  
## <a name="remarks"></a>Uwagi  
 Spójne wyniki, można interpretować `BOOL` wartości, tak aby wartość różną od zera wartości są `TRUE` i zero jest `FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
