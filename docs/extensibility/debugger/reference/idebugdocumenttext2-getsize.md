---
title: 'IDebugDocumentText2:: GetSize | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731592"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Pobiera rozmiar tekstu w tym miejscu dokumentu.

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
określoną Zwraca liczbę wierszy tekstu.

`pcNumChars`\
określoną Zwraca liczbę znaków tekstu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

 [Tylko C++] Jeśli określona wartość nie jest wymagana, należy przekazać wartość NULL dla parametru.

 [Tylko w C#] Należy określić oba parametry.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
