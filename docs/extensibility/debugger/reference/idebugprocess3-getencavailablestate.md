---
title: IDebugProcess3::GetENCAvailableState | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc51b89061dca3c0d3026b391b8d6b0106421542
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202347"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Ta metoda pobiera bieżący stan Edytuj i Kontynuuj proces. Dostawcy niestandardowego portu powinna zawsze zwracać `E_NOTIMPL`.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parametry
`pReason`\
[out] Wartość z zakresu od [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Dostawcy niestandardowego portu powinna zawsze zwracać `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi
 Ten stan może mieć wpływ [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Zobacz także
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)