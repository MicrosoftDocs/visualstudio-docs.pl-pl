---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1869b9b4bda263d72db9c949be730e51fdc02d01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323900"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Pobiera informacji na temat tego, czy moduł reprezentuje kod użytkownika, czy nie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parametry
`pfUser`\
[out] Wartość różną od zera (`TRUE`) moduł reprezentuje kod użytkownika, wartość zero (`FALSE`) Jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)