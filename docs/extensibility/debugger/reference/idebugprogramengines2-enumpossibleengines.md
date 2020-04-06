---
title: IDebugProgramEngines2::EnumPossibleEngines | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722431"
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
[w] Liczba identyfikatorów GUID DE do zwrócenia. Określa również maksymalny rozmiar `rgguidEngines` tablicy.

`rgguidEngines`\
[w, na zewnątrz] Tablica identyfikatorów GUID DE do wypełnienia.

`pceltEngines`\
[na zewnątrz] Zwraca rzeczywistą liczbę identyfikatorów GUID DE, które są zwracane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` lub [C#] 0x8007007A, jeśli bufor nie jest wystarczająco duży.

## <a name="remarks"></a>Uwagi
 Aby określić, ile istnieje aparatów, wywołaj `celtBuffer` tę metodę raz `rgguidEngines` z parametrem ustawionym na 0 i parametrem ustawionym na wartość null. `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` Zwraca (0x8007007A dla języka C#), a `pceltEngines` parametr zwraca wymagany rozmiar buforu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
