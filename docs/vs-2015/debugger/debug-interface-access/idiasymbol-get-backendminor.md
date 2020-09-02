---
title: 'IDiaSymbol:: get_backEndMinor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db90118a1c8d235637f78edd9daa51f3531c628d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827108"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera wewnętrzny numer wersji kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 określoną Zwraca numer wersji pomocniczej zaplecza. Zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator zwykle składa się z dwóch głównych elementów: fronton (Parser), który obsługuje Analizowanie kodu źródłowego w postaci pośredniej i zaplecza (Generator kodu), który konwertuje pośredni formularz do zestawu. Nie zdarza się, że fronton nie ma innej wersji niż zaplecze.  
  
 Numer wersji frontonu lub zaplecza składa się z trzech części: \<major> . \<minor> . \<build> , gdzie \<major> jest głównym numerem wersji, \<minor> jest numerem wersji pomocniczej i \<build> jest numerem kompilacji. Na przykład 13.10.3077.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówki|dia2. h|  
|Wersja:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
