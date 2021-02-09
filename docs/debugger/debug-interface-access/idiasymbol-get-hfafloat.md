---
title: 'IDiaSymbol:: get_hfaFloat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaFloat method
ms.assetid: 73ddcffe-cdac-4b03-be42-82ef985d17ee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f76bcfee990ac6fc55f97480886f751ae24bc00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854207"
---
# <a name="idiasymbolget_hfafloat"></a>IDiaSymbol::get_hfaFloat
Pobiera flagę, która określa, czy typ zdefiniowany przez użytkownika (UDT) zawiera jednorodne dane agregacji zmiennoprzecinkowej (HFA) typu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hfaFloat( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy UDT zawiera dane HFA typu float; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)