---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810332"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa konwencję wywoływania dla funkcji.  
  
> [!NOTE]
> Tutaj opisano tylko najczęstsze wartości wyliczenia. Pełne Wyliczenie jest dostępne w pliku nagłówkowym cvconst. h.  
  
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
 Określa konwencję wywoływania funkcji przy użyciu wypychania od prawej do lewej. Funkcja wywołująca czyści stos.  
  
 CV_CALL_NEAR_FAST  
 Określa konwencję wywoływania funkcji używającą niemal od lewej do prawej wypychania z rejestrami. Wywołana funkcja używa sumy parametrów bajtów do wyczyszczenia stosu.  
  
 CV_CALL_NEAR_STD  
 Określa konwencję wywoływania funkcji przy użyciu wywołania blisko standardowego (wypychania od prawej do lewej).  
  
 CV_CALL_NEAR_SYS  
 Określa konwencję wywoływania funkcji przy użyciu wywołania blisko systemu.  
  
 CV_CALL_THISCALL  
 Określa konwencję wywoływania funkcji przy użyciu `this` wywołania ( `this` wskaźnik przeszedł do rejestru).  
  
 CV_CALL_CLRCALL  
 Określa konwencję wywoływania funkcji używaną przez środowisko uruchomieniowe języka wspólnego (CLR) (znaną również jako konwencja wywoływania kodu zarządzanego).  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
