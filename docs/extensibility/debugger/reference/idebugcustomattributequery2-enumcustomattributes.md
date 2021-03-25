---
description: Pobiera moduł wyliczający dla wszystkich atrybutów niestandardowych dołączonych do tego pola.
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcd11f3058de191a3b0a77f0316afb6140769fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077645"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Pobiera moduł wyliczający dla wszystkich atrybutów niestandardowych dołączonych do tego pola.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
określoną Zwraca obiekt [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) reprezentujący listę atrybutów niestandardowych; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych atrybutów niestandardowych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub S_FALSE, jeśli nie ma żadnych atrybutów niestandardowych tego pola. W przeciwnym razie zwraca kod błędu;

## <a name="remarks"></a>Uwagi
 Pole może mieć wiele atrybutów niestandardowych.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
