---
description: Pobiera ciąg programu, który jest używany do obliczenia zestawu rejestru przed wywołaniem bieżącej funkcji.
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3e16503d025771b3af34c7f4eee185c2f6aacab
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148494"
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
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ciąg programu jest sekwencją makr, które są interpretowane w celu ustalenia prologu. Na przykład typowa Ramka stosu może używać ciągu programu `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Format jest odwrotnym zapisem polskim, gdzie operatory obserwują operandy. `T0` reprezentuje zmienną tymczasową na stosie. W tym przykładzie wykonywane są następujące czynności:

1. Przenieś zawartość rejestru `ebp` do programu `T0` .

2. Dodaj `4` do wartości w programie `T0` , aby utworzyć adres, Pobierz wartość z tego adresu i Zapisz wartość w rejestrze `eip` .

3. Pobierz wartość z adresu przechowywanego w `T0` i Zapisz tę wartość w rejestrze `ebp` .

4. Dodaj `8` do wartości w `T0` i Zapisz tę wartość w rejestrze `esp` .

   Należy zauważyć, że ciąg programu jest specyficzny dla procesora i do konwencji wywoływania dla funkcji reprezentowanej przez bieżącą ramkę stosu.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
