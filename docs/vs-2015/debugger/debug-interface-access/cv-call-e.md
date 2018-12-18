---
title: Cv_call_e — | Dokumentacja firmy Microsoft
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
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f687c9d95444fdad35213b86af2c3ee1a252544e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726966"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa konwencję wywołania funkcji.  
  
> [!NOTE]
>  Tylko najbardziej typowych wartości wyliczenia są opisane tutaj. Pełne wyliczenia jest dostępna w pliku nagłówkowym cvconst.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementy  
 CV_CALL_NEAR_C  
 Określa Konwencję wywoływania funkcji przy użyciu prawie wypychane od prawej do lewej. Funkcja wywołująca czyści stos.  
  
 CV_CALL_NEAR_FAST  
 Określa Konwencję wywoływania funkcji za pomocą rejestrów przy użyciu prawie wypychane od lewej do prawej. Wywołana funkcja używa Suma bajtów parametrów można wyczyścić stosu.  
  
 CV_CALL_NEAR_STD  
 Określa Konwencję wywoływania funkcji przy użyciu prawie standardowe wywołanie (push od prawej do lewej).  
  
 CV_CALL_NEAR_SYS  
 Określa Konwencję wywoływania funkcji przy użyciu prawie wywołanie systemowe.  
  
 CV_CALL_THISCALL  
 Określa Konwencję wywoływania funkcji przy użyciu `this` wywołania (`this` wskaźnik przekazywane w rejestrze).  
  
 CV_CALL_CLRCALL  
 Określa Konwencję wywoływania funkcji używane przez wspólnego języka środowiska uruchomieniowego (CLR) (znany także jako kod zarządzany Konwencja wywoływania).  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez wywołanie [idiasymbol::get_callingconvention —](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)



