---
title: IDebugProgramEngines2::EnumPossibleEngines | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 532486c66b6feb5c397b9167e2b1cd6197513fa8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343399"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Zwraca identyfikator GUID w faktycznej dla wszystkich możliwych silniki debugowania (DE), które można debugować ten program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parametry
`celtBuffer`\
[in] Liczba identyfikatorów GUID DE do zwrócenia. Maksymalny rozmiar to określa również `rgguidEngines` tablicy.

`rgguidEngines`\
[out w] Tablica identyfikatorów GUID DE do wypełnienia.

`pceltEngines`\
[out] Zwraca aktualną liczbę identyfikatorów GUID DE, które są zwracane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` lub [C#] 0x8007007A, jeśli bufor nie jest wystarczająco duży.

## <a name="remarks"></a>Uwagi
 Aby ustalić, ile aparaty są, wywoływanie tej metody raz z `celtBuffer` parametru równa 0 i `rgguidEngines` zestaw parametrów ma wartość null. Spowoduje to zwrócenie `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A dla języka C#) i `pceltEngines` parametr zwraca niezbędne rozmiar buforu.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)