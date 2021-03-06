---
description: Pobiera zakres kodu źródłowego tego kontekstu dokumentu.
title: 'IDebugDocumentContext2:: GetSourceRange — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a66f1b99793b1c8fa8036771d7815f95a395462a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066597"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Pobiera zakres kodu źródłowego tego kontekstu dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametry
`pBegPosition`\
[in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana początkową pozycją. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.

`pEndPosition`\
[in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana pozycją końcową. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakres źródłowy to cały zakres kodu źródłowego od bieżącej instrukcji z powrotem do tuż po poprzedniej instrukcji, która przyczynia się do wykonania kodu. Zakres źródłowy jest zazwyczaj używany do mieszania instrukcji źródłowych, w tym komentarzy, z kodem w oknie demontażu.

 Aby uzyskać zakres dla tylko instrukcji kodu zawartych w tym kontekście dokumentu, wywołaj metodę [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
