---
title: IDebugProgram2::GetENCUpdate | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722837"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Ta metoda pobiera aktualizację Edytuj i kontynuuj (ENC) dla tego programu. Niestandardowy aparat debugowania zawsze zwraca `E_NOTIMPL`.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parametry
`ppUpdate`\
[na zewnątrz] Zwraca wewnętrzny interfejs, który może służyć do aktualizacji tego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Niestandardowy aparat debugowania `E_NOTIMPL`powinien zawsze zwracać .

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
