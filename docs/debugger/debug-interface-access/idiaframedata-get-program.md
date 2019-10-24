---
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743518"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Pobiera ciąg programu, który jest używany do obliczenia zestawu rejestru przed wywołaniem bieżącej funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca ciąg programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ciąg programu jest sekwencją makr, które są interpretowane w celu ustalenia prologu. Na przykład typowa Ramka stosu może używać ciągu programu `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Format jest odwrotnym zapisem polskim, gdzie operatory obserwują operandy. `T0` reprezentuje zmienną tymczasową na stosie. W tym przykładzie wykonywane są następujące czynności:

1. Przenieś zawartość rejestru `ebp`, aby `T0`.

2. Dodaj `4` do wartości w `T0`, aby utworzyć adres, Pobierz wartość z tego adresu i Zapisz wartość w `eip`register.

3. Pobierz wartość z adresu przechowywanego w `T0` i Zapisz tę wartość w `ebp`rejestru.

4. Dodaj `8` do wartości w `T0` i Zapisz tę wartość w `esp`register.

   Należy zauważyć, że ciąg programu jest specyficzny dla procesora i do konwencji wywoływania dla funkcji reprezentowanej przez bieżącą ramkę stosu.

## <a name="see-also"></a>Zobacz także
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)