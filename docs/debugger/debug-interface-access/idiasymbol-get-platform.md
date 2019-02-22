---
title: IDiaSymbol::get_platform | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bbcad8902a2c3ce86b1127d9317a3901c655372
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639456"
---
# <a name="idiasymbolgetplatform"></a>IDiaSymbol::get_platform
Pobiera typ platformy, dla którego compiland — został skompilowany.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_platform ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca wartość z zakresu od [cv_cpu_type_e — wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md) wpisz został skompilowany compiland — wyliczenie, które określa platformę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_CPU_TYPE_e, wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md)