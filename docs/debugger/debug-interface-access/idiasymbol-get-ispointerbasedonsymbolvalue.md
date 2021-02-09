---
title: 'IDiaSymbol:: get_isPointerBasedOnSymbolValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55d27f9f3f2054e4093eccfd40d75dbb7c9a6721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863138"
---
# <a name="idiasymbolget_ispointerbasedonsymbolvalue"></a>IDiaSymbol::get_isPointerBasedOnSymbolValue
Określa, czy `this` wskaźnik jest oparty na wartości symbolicznej.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isPointerBasedOnSymbolValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do elementu `BOOL` , który określa, czy `this` wskaźnik jest oparty na wartości symbolicznej.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)