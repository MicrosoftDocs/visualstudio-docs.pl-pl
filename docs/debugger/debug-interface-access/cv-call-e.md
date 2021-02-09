---
title: CV_call_e | Microsoft Docs
description: Pobierz informacje referencyjne na temat CV_call_e typu wyliczeniowego, który określa konwencję wywoływania dla funkcji w zestawie SDK dostępu do interfejsu debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a40710026b00f46f6539ad73a938999440f30b02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865455"
---
# <a name="cv_call_e"></a>CV_call_e
Określa konwencję wywoływania dla funkcji.

> [!NOTE]
> Tutaj opisano tylko najczęstsze wartości wyliczenia. Pełne Wyliczenie jest dostępne w pliku nagłówkowym cvconst. h.

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
CV_CALL_NEAR_C określa konwencję wywoływania funkcji przy użyciu opcji niemal od prawej do lewej. Funkcja wywołująca czyści stos.

CV_CALL_NEAR_FAST określa konwencję wywoływania funkcji, używając niemal od lewej do prawej wypychania z rejestrami. Wywołana funkcja używa sumy parametrów bajtów do wyczyszczenia stosu.

CV_CALL_NEAR_STD określa konwencję wywoływania funkcji przy użyciu wywołania blisko standardowego (wypychania od prawej do lewej).

CV_CALL_NEAR_SYS określa konwencję wywoływania funkcji przy użyciu wywołania blisko systemu.

CV_CALL_THISCALL określa konwencję wywoływania funkcji przy użyciu `this` wywołania ( `this` wskaźnik przeszedł do rejestru).

CV_CALL_CLRCALL określa konwencję wywoływania funkcji używaną przez środowisko uruchomieniowe języka wspólnego (CLR) (znaną również jako konwencja wywoływania kodu zarządzanego).

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
