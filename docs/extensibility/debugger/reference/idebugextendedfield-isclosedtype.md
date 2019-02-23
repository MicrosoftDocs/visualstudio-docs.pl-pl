---
title: IDebugExtendedField::IsClosedType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9056a3543de27b26bc32eec5840248c337ea11fa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678335"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Określa, czy pole reprezentuje zamkniętego typu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli to pole jest zamkniętego typu, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.

## <a name="see-also"></a>Zobacz też
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)