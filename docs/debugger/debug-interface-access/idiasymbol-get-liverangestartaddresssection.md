---
title: IDiaSymbol::get_liveRangeStartAddressSection | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 596f7a3c8371007787fc3531abd1bea7892c1ca6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918767"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Zwraca część sekcji adres początkowy zakresu, w którym symbolu lokalnego jest poprawna.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `section`  
 [out] Zwraca część sekcji początkowy zakresu adresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Zwrócony kod błędu: oznacza, że symbol nie ma informacji o zakresie na żywo.  
  
## <a name="remarks"></a>Uwagi  
 Adres utworzone przez sekcję i przesunięcie to początek zakresu, w którym symbol jest poprawna.  
  
 Aby uzyskać przesunięcia częściami składowymi adresu, użyj [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia100.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)