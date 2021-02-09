---
title: 'IDiaSymbol:: get_lowerBoundId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBoundId method
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1780a1ec3af3a066bae698d7e2b0db8b25c4e69b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853885"
---
# <a name="idiasymbolget_lowerboundid"></a>IDiaSymbol::get_lowerBoundId
Pobiera identyfikator symbolu dolnej granicy wymiaru tablicy Pascal.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lowerBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca identyfikator symbolu symbolu, który reprezentuje dolną granicę wymiaru tablicy Pascal.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Identyfikator jest unikatową wartością utworzoną przez DIA SDK, aby oznaczyć wszystkie symbole jako unikatowe.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)