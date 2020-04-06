---
title: IDebugPortSupplier3::EnumPersistedPorts | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92b31a6b6898b0031e4a01d5a6433d0ce77e64f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724451"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Ta metoda pobiera obiekt, który umożliwia wyliczenie listy utrwalonych portów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`PortNames`\
[w] Struktura [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) zawierająca listę nazw portów do znalezienia i zwrócenia między utrwalonych portów. Tylko te utrwalone porty o tych nazwach zostaną zwrócone.

`ppEnum`\
[na zewnątrz] Obiekt, który implementuje interfejs [IEnumDebugPorts2.](../../../extensibility/debugger/reference/ienumdebugports2.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Utrwalone porty są ładowane, gdy dostawca portu jest tworzone i zapisywane, gdy dostawca portu jest niszczony.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
