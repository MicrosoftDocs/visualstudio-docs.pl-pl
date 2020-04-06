---
title: IDebugAddress::GetAddress | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736606"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Zwraca strukturę opisującą obiekt i jego lokalizację w jego zakresie lub kontenerze.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[w, na zewnątrz] Struktura [DEBUG_ADDRESS,](../../../extensibility/debugger/reference/debug-address.md) która jest wypełniona tą metodą.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Struktura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) jest przekazywana do tej metody, która następnie wypełnia ją odpowiednimi informacjami. Sposób interpretacji tych informacji zależy od rodzaju zwracanych informacji i samego programu obsługi symboli. Zobacz [DEBUG_ADDRESS,](../../../extensibility/debugger/reference/debug-address.md) aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
