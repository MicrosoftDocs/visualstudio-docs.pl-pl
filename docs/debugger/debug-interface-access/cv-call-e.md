---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8c11e84a514739049a044a12ae482f7b2d9929
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316195"
---
# <a name="cvcalle"></a>CV_call_e
Określa konwencję wywołania funkcji.

> [!NOTE]
> Tylko najbardziej typowych wartości wyliczenia są opisane tutaj. Pełne wyliczenia jest dostępna w pliku nagłówkowym cvconst.h.

## <a name="syntax"></a>Składnia

```C++
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
