---
description: Ta metoda pobiera wyjątek skojarzony z obiektem, jeśli istnieje.
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ec511cc6145c890c4f62a76563c51aa7c667977
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167636"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Ta metoda pobiera wyjątek skojarzony z obiektem, jeśli istnieje.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parametry
`ppException`\
określoną Zwraca obiekt reprezentujący wyjątek.

`ppField`\
określoną Zwraca obiekt reprezentujący określone pole, które mogło być przyczyną wyjątku (może to być wartość null).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Aby sprawdzić, czy występuje wyjątek, sprawdź wartość zwróconą przez `ppException` : Jeśli jest to wartość null, żaden wyjątek nie jest skojarzony z tym obiektem.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
