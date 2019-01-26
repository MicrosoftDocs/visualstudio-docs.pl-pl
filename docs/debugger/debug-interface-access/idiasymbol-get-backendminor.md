---
title: Idiasymbol::get_backendminor — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a065a2a6d866e99f0576727febad684e78225b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973281"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Pobiera zaplecza pomocniczy numer wersji kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer wersji pomocniczej zaplecza. Zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Kompilatora zwykle składa się z dwóch podstawowe elementy: fronton (analizatora), która obsługuje analizowania kodu źródłowego w formie pośredniego, i zapleczem (generator kodu) konwertująca pośrednich formularza do zestawu. Nie jest niczym niezwykłym frontonu do innej wersji niż zaplecza.  
  
 Frontonu lub zaplecza numer wersji składa się z trzech części: \<główna >.\< pomocnicza >. \<kompilacji >, gdzie \<główne > jest główny numer wersji, \<pomocnicza > jest numerem wersji pomocniczej i \<kompilacji > jest numerem kompilacji. Na przykład 13.10.3077.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)