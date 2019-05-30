---
title: IDebugGenericFieldInstance::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7fbd896e2798ed42c382d9975ec70a7e8aebbd7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351229"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
Pobiera argumenty parametrów typu dla tego wystąpienia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeArguments(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   ULONG32*      pcArgs
);
```

```csharp
int GetTypeArguments(
   uint              cArgs,
   out IDebugField[] ppArgs,
   ref uint          pcArgs
);
```

## <a name="parameters"></a>Parametry
`cArgs`\
[in] Liczba parametrów typu.

`ppArgs`\
[out] Zwraca tablicę parametrów typu.

`pcArgs`\
[out w] Liczba elementów członkowskich w `ppArgs` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)