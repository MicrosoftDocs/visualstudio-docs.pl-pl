---
title: Idiasymbol::get_addressoffset — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d41f309f8716f71e6c896cb75163b0a79cd31ef
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810313"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera przesunięcia część adresu. Zastosowania [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsStatic`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca przesunięcia część adresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Dla statycznych elementów członkowskich znajdujących się w zewnętrznej bibliotece DLL przesunięcie zwracanego przez tę metodę może mieć wartość 0, ponieważ ta metoda zależy od tego, uzyskiwanie adresu wirtualnego elementu członkowskiego. Wirtualne adresy są prawidłowe tylko wtedy, gdy [idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) method in Class metoda [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu została wywołana z parametrem wartość różną od zera, określając adres obciążenia biblioteki dll.  
  
 Aby uzyskać sekcji część adresu, należy wywołać [idiasymbol::get_addresssection —](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) metody.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Idiasymbol::get_addresssection —](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasession::put_loadaddress —](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



