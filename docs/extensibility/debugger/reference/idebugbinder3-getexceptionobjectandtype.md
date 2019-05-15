---
title: IDebugBinder3::GetExceptionObjectAndType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22d048bb915146e6c966dd16ca3b2345b5d697ba
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614730"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Ta metoda pobiera wyjątku skojarzonego z obiektem, jeśli istnieje.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parametry
`ppException`\
[out] Zwraca obiekt reprezentujący wyjątek.

`ppField`\
[out] Zwraca obiekt reprezentujący określonego pola, które mogą być przyczyną wyjątku (może to być wartość null).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Aby sprawdzić, czy występuje wyjątek, należy sprawdzić wartość zwrócona przez obiekt `ppException`: Jeśli jest to wartość null, wówczas żaden wyjątek nie jest skojarzony z tym obiektem.

## <a name="see-also"></a>Zobacz także
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)