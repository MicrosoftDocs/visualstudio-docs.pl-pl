---
description: Ta metoda pobiera obiekt, który umożliwia Wyliczenie listy utrwalonych portów.
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4fe55898f6dbc7713db6e013868b1c7f22a5faf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071964"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Ta metoda pobiera obiekt, który umożliwia Wyliczenie listy utrwalonych portów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`PortNames`\
podczas Struktura [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) , która zawiera listę nazw portów do znalezienia i zwrócenia wśród utrwalonych portów. Zostaną zwrócone tylko te utrwalone porty z tymi nazwami.

`ppEnum`\
określoną Obiekt, który implementuje interfejs [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Utrwalone porty są ładowane podczas tworzenia wystąpienia dostawcy portów i zapisywane, gdy dostawca portu jest niszczony.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
