---
title: IDiaSymbol::get_numberOfColumns | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c6078cd1246e5bcb13938e31f65e67f5615e4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953199"
---
# <a name="idiasymbolgetnumberofcolumns"></a>IDiaSymbol::get_numberOfColumns
Pobiera liczbę kolumn w macierzy.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_numberOfColumns(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `DWORD` przechowuje liczbę kolumn w macierzy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)