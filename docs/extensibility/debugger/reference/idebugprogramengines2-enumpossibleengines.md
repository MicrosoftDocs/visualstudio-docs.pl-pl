---
description: Zwraca identyfikatory GUID dla wszystkich możliwych aparatów debugowania (DE), które mogą debugować ten program.
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a49a0590a1ec2f0b0e7d2be59fe2161b438154a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084210"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Zwraca identyfikatory GUID dla wszystkich możliwych aparatów debugowania (DE), które mogą debugować ten program.

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
podczas Liczba wszystkich identyfikatorów GUID do zwrócenia. Określa również maksymalny rozmiar `rgguidEngines` tablicy.

`rgguidEngines`\
[in. out] Tablica wszystkich identyfikatorów GUID do wypełnienia.

`pceltEngines`\
określoną Zwraca rzeczywistą liczbę zwracanych identyfikatorów GUID.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` lub [C#] 0x8007007A, jeśli bufor nie jest wystarczająco duży.

## <a name="remarks"></a>Uwagi
 Aby określić liczbę aparatów, należy wywołać tę metodę raz z `celtBuffer` parametrem ustawionym na 0, a `rgguidEngines` parametr ustawiony na wartość null. To zwraca `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A for C#), a `pceltEngines` parametr zwraca wymagany rozmiar buforu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
