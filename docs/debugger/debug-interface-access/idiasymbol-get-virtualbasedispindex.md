---
title: Idiasymbol::get_virtualbasedispindex — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseDispIndex method
ms.assetid: 5561a3cb-2c82-41cf-9217-3ee2b1e1d1d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ad15c3474157f9858c4647c47249121bd386d9a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612845"
---
# <a name="idiasymbolgetvirtualbasedispindex"></a>IDiaSymbol::get_virtualBaseDispIndex
Pobiera indeks symbolu w tabeli wirtualnej przemieszczenia podstawowej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_virtualBaseDispIndex (
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca indeks do tabeli wirtualnej przemieszczenia podstawowej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)