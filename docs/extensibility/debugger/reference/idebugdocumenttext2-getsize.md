---
title: IDebugDocumentText2::GetSize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9207858bd43809cbc070935ae2f53f354d9d6f9b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199156"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Pobiera rozmiar tekstu, w tym miejscu w dokumencie.

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
[out] Zwraca liczbę wierszy tekstu.

`pcNumChars`\
[out] Zwraca liczbę znaków tekstu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

 [C++ tylko] Jeśli określonej wartości nie jest wymagana, należy przekazać wartość NULL dla parametru.

 [C# tylko] Oba parametry muszą być określone.

## <a name="see-also"></a>Zobacz także
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)