---
title: IDiaSymbol::get_registerType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f714e5637776d6a0606246d339d3f9d2ccd9f19a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62835542"
---
# <a name="idiasymbolgetregistertype"></a>IDiaSymbol::get_registerType
Pobiera typ rejestru.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_registerType(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Wskaźnik do `DWORD` zawierający typ rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)