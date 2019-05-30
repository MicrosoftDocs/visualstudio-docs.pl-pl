---
title: IDebugField::GetSize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db4ef8a41ec6759194cc35203b6458c7688f4322
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333205"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Ta metoda pobiera rozmiar pola, w bajtach.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametry
`pdwSize`\
[out] Zwraca rozmiar.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszystkie pola mają typ, a wszystkie typy mają rozmiar. Na przykład pole z typem bajtów ma rozmiar 1 bajt.

## <a name="see-also"></a>Zobacz także
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)