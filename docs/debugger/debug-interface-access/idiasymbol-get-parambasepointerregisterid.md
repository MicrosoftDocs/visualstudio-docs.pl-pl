---
title: IDiaSymbol::get_paramBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bda768518c140f0f30d6ab4553ba16b3f519651c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628037"
---
# <a name="idiasymbolgetparambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
Pobiera identyfikator rejestru, który zawiera podstawowy wskaźnik do parametrów. Zastosowania [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) ustawiono `SymTagFunction`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_paramBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca identyfikator rejestru, który zawiera podstawowy wskaźnik do parametrów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania
 Nagłówek: Dia2.h

 Biblioteka: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)