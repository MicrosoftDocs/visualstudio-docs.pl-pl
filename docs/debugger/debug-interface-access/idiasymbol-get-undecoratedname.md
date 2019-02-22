---
title: Idiasymbol::get_undecoratedname — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedName method
ms.assetid: e49edf25-a51d-4787-bd5b-2bf5af827c8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed4826b61bb63993faed0dfebe113a89213d91b7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626456"
---
# <a name="idiasymbolgetundecoratedname"></a>IDiaSymbol::get_undecoratedName
Pobiera nieozdobioną nazwę zawartej dekorowane, C++ lub połączenia, nazwa.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_undecoratedName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca nazwy ozdobionej nieozdobioną nazwę zawartej w języku C++.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)