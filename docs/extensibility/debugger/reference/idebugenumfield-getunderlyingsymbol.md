---
description: Ta metoda zwraca IDebugField, który reprezentuje nazwę wyliczenia.
title: 'IDebugEnumField:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9343c1b0908c6b132ea982a46623b8c1cf20efc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092569"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Ta metoda zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje nazwę wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
określoną Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujący nazwę tego wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa wyliczenia zawiera również typ wyliczenia, który jest powiązany z lokalizacją w pamięci za pomocą elementu [bind](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Węglowodor](../../../extensibility/debugger/reference/idebugbinder-bind.md)
