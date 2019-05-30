---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f1a92cc5e595bd2574174f0d0776c6605e42da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337012"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Zwraca liczbę typu argumenty parametrów dla tego wystąpienia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parametry
`pcArgs`\
[out w] Liczba argumentów do parametrów typu dla tego wystąpienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Na przykład jeśli lista\<int >, ta metoda zwraca wartość 1 i, jeśli lista\<int, float2 > Ta metoda zwraca wartość 2. Ta metoda zwraca wartość 0, jeśli nie wymaga argumentów typu.

## <a name="see-also"></a>Zobacz także
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)