---
title: IDebugDocumentContext2::Szukaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435bb2d5402be06a5fcb3ff9fc99a5c5cb8cb3ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731749"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Przenosi kontekst dokumentu o daną liczbę instrukcji lub wierszy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametry
`nCount`\
[w] Liczba instrukcji lub wierszy do przodu, w zależności od kontekstu dokumentu.

`ppDocContext`\
[na zewnątrz] Zwraca nowy [obiekt IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) z nową pozycją.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
