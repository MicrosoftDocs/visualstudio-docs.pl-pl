---
title: IDebugDocumentContext2::Porównaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731881"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porównuje ten kontekst dokumentu z daną tablicą kontekstów dokumentu.

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
[w] Wartość z [wyliczenia DOCCONTEXT_COMPARE,](../../../extensibility/debugger/reference/doccontext-compare.md) która określa typ porównania.

`rgpDocContextSet`\
[w] Tablica [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiektów, które reprezentują konteksty dokumentu porównywane do.

`dwDocContextSetLen`\
[w] Długość tablicy kontekstów dokumentu do porównania.

`pdwDocContext`\
[na zewnątrz] Zwraca indeks do `rgpDocContextSet` tablicy pierwszego kontekstu dokumentu, który spełnia porównania.

## <a name="return-value"></a>Wartość zwracana
 Zwraca, `S_OK` jeśli znaleziono dopasowanie. Zwraca, `S_FALSE` jeśli nie znaleziono dopasowania. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekty, które są przekazywane w tablicy musi być zaimplementowana przez ten sam aparat debugowania, który implementuje `IDebugDocumentContext2` obiekt jest wywoływany na; w przeciwnym razie porównanie jest nieprawidłowe.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
