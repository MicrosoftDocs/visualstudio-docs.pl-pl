---
title: IDebugField::Równe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729009"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Ta metoda porównuje to pole z określonym polem równości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parametry
`pField`\
[w] Pole do porównania z tym.

## <a name="return-value"></a>Wartość zwracana
 Jeśli pola są takie `S_OK`same, zwraca wartość . Jeśli pola są różne, zwraca `S_FALSE.` inaczej, zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
