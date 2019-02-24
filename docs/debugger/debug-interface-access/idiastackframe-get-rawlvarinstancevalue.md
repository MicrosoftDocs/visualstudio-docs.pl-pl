---
title: Idiastackframe::get_rawlvarinstancevalue — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8ad236307360a96f64999313764424305980fc9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624025"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Ta metoda pobiera wartość określonej zmiennej lokalnej, jako bajtów raw.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parametry
 `pInstance`

[in] `IDiaLVarInstance` Obiekt reprezentujący wystąpienie zmiennej lokalnej, aby uzyskać wartość.

 `cbDataMax`

[in] Maksymalna liczba bajtów w buforze wskazywany przez `pbData`. Może to być maksymalnie 8 bajtów (`sizeof(ULONGLONG)`).

 `pcbData`

[out] Zwraca wartość rzeczywista liczba bajtów przechowywanych w buforze.

 `pbData`

[out] Bufor w celu wprowadzenia danych. Nie może to być `NULL`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)