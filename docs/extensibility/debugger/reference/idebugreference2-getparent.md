---
title: IDebugReference2::GetParent | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddef1d78d64f0e034aed9d48b59bf3e46ccba24f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339807"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Pobiera odniesienie nadrzędne odwołanie. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

## <a name="parameters"></a>Parametry
`ppParent`\
[out] Zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt, który reprezentuje element nadrzędny tej właściwości.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)