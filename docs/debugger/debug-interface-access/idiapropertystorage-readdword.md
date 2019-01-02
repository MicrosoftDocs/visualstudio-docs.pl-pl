---
title: IDiaPropertyStorage::ReadDWORD | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed37f7f8126f5477fb63304ea6b6248cba190679
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828280"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Odczytuje `DWORD` wartości w zbiorze właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator właściwości do odczytu (`PROPID` jest zdefiniowany w WTypes.h jako `ULONG`).  
  
 `pValue`  
 [out] Zwraca wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` Jeśli właściwość nie jest typu `DWORD`.  
  
## <a name="remarks"></a>Uwagi  
 Element `DWORD` jest definiowany przez Windows jako 32-bitowa liczba całkowita bez znaku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)