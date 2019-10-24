---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
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
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741635"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Ta metoda pobiera wartość określonej zmiennej lokalnej jako nieprzetworzone bajty.

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

podczas Obiekt `IDiaLVarInstance` reprezentujący wystąpienie zmiennej lokalnej, dla którego ma zostać uzyskana wartość.

 `cbDataMax`

podczas Maksymalna liczba bajtów w buforze wskazywanym przez `pbData`. Może to być maksymalnie 8 bajtów (`sizeof(ULONGLONG)`).

 `pcbData`

określoną Zwraca rzeczywistą liczbę bajtów przechowywanych w buforze.

 `pbData`

określoną Bufor, który ma zostać wypełniony danymi. Nie można `NULL`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)