---
description: Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentów.
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a680da6f33d3da37995eb26071c0ea5f1ddc2283
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066714"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parametry
`compare`\
podczas Wartość z wyliczenia [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) , która określa typ porównania.

`rgpDocContextSet`\
podczas Tablica obiektów [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , które reprezentują konteksty dokumentu porównywane z.

`dwDocContextSetLen`\
podczas Długość tablicy kontekstów dokumentu do porównania.

`pdwDocContext`\
określoną Zwraca indeks do `rgpDocContextSet` tablicy pierwszego kontekstu dokumentu, który spełnia porównanie.

## <a name="return-value"></a>Wartość zwracana
 Zwraca `S_OK` Czy znaleziono dopasowanie. Zwraca wartość, `S_FALSE` Jeśli nie znaleziono żadnego dopasowania. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekty [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , które są przesyłane w tablicy, muszą być zaimplementowane przez ten sam aparat debugowania, który implementuje `IDebugDocumentContext2` obiekt wywoływany; w przeciwnym razie porównanie jest nieprawidłowe.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
