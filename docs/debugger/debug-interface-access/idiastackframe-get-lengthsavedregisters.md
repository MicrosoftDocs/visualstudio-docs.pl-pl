---
title: Idiastackframe::get_lengthsavedregisters — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthSavedRegisters method
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936cd1f057258bdeda455c67e69e3cd7a9272cc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839052"
---
# <a name="idiastackframegetlengthsavedregisters"></a>IDiaStackFrame::get_lengthSavedRegisters
Pobiera liczba bajtów zapisanych rejestrów wypychane na stos.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_lengthSavedRegisters ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca liczbę bajtów zapisanych rejestrów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)