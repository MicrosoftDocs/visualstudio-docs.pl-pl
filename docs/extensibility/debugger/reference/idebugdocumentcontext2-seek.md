---
description: Przenosi kontekst dokumentu o określoną liczbę instrukcji lub wierszy.
title: 'IDebugDocumentContext2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9fcc430102ec974f2492a8e65894faa45978693
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066558"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Przenosi kontekst dokumentu o określoną liczbę instrukcji lub wierszy.

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
podczas Liczba instrukcji lub wierszy, które mają zostać przesunięte w przód, w zależności od kontekstu dokumentu.

`ppDocContext`\
określoną Zwraca nowy obiekt [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) z nową pozycją.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
