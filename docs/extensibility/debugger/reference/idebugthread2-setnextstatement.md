---
description: Ustawia bieżący wskaźnik instrukcji do danego kontekstu kodu.
title: 'IDebugThread2:: SetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dd6bd027a9938b7dce855742cc351180498bb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081168"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Ustawia bieżący wskaźnik instrukcji do danego kontekstu kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parametry
`pStackFrame`\
Zarezerwowane do użytku w przyszłości; Ustaw wartość null.

`pCodeContext`\
podczas Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który opisuje lokalizację kodu do wykonania i jego kontekst.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono inne możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Następna instrukcja nie może znajdować się w ramce stosu głębiej na stosie ramek.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Następna instrukcja nie jest skojarzona z żadną ramką w stosie.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Niektóre aparaty debugowania nie mogą ustawić następnej instrukcji po wystąpieniu wyjątku.|

## <a name="remarks"></a>Uwagi
 Wskaźnik instrukcji wskazuje następną instrukcję lub instrukcji do wykonania. Ta metoda służy do ponowienia próby wykonania wiersza kodu źródłowego lub wymuszenia wykonywania operacji w innej funkcji, na przykład.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
