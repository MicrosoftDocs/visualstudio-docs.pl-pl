---
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725626"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Ta metoda zwraca typ obiektu, do którego wskazuje ten obiekt wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
określoną Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisującą typ obiektu docelowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli na przykład obiekt [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) wskazuje liczbę całkowitą, typ [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zwracany przez tę metodę opisuje ten typ liczba całkowita.

## <a name="see-also"></a>Zobacz też
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
