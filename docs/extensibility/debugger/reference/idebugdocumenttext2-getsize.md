---
title: Tekst IDebugDocumentText2::GetSize | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731592"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Pobiera rozmiar tekstu w tym miejscu w dokumencie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parametry
`pcNumLines`\
[na zewnątrz] Zwraca liczbę wierszy tekstu.

`pcNumChars`\
[na zewnątrz] Zwraca liczbę znaków tekstu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

 [Tylko C++] Jeśli określona wartość nie jest pożądana, przekaż wartość NULL dla parametru.

 [Tylko C#] Oba parametry muszą być określone.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
