---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 5a45568ea62a767d06a33c324f0f05a1f697e93f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464983"
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

podczas `IDiaLVarInstance` Obiekt reprezentujący wystąpienie zmiennej lokalnej, dla którego ma zostać uzyskana wartość.

 `cbDataMax`

podczas Maksymalna liczba bajtów w buforze wskazywanym przez `pbData` . Może to być maksymalnie 8 bajtów ( `sizeof(ULONGLONG)` ).

 `pcbData`

określoną Zwraca rzeczywistą liczbę bajtów przechowywanych w buforze.

 `pbData`

określoną Bufor, który ma zostać wypełniony danymi. Nie może to być `NULL` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)