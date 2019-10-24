---
title: 'IDiaSymbol:: get_sizeInUdt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87f6e6ea3118aa7c278bc83a69a290176b267c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739330"
---
# <a name="idiasymbolget_sizeinudt"></a>IDiaSymbol::get_sizeInUdt
Pobiera rozmiar elementu członkowskiego typu zdefiniowanego przez użytkownika.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_sizeInUdt(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `DWORD`, który określa rozmiar elementu członkowskiego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)