---
title: Idiaframedata::get_lengthsavedregisters — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthSavedRegisters method
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e05ebb4d7a58be353bb933a4ce5e5053d8dbf33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839943"
---
# <a name="idiaframedatagetlengthsavedregisters"></a>IDiaFrameData::get_lengthSavedRegisters
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
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartość zwrócona przez tę metodę jest zwykle używanych w interpretacji ciągu program (zobacz [idiaframedata::get_program —](../../debugger/debug-interface-access/idiaframedata-get-program.md) metody dla definicji ciąg program).

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)