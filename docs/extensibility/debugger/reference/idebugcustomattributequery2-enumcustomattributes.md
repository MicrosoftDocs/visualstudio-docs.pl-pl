---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aade3935a49af176220e800647e6e821054bbb48
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875961"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Pobiera moduł wyliczający dla wszystkich atrybutów niestandardowych, dołączony do tego pola.

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

#### <a name="parameters"></a>Parametry
 `ppEnum`

 [out] Zwraca [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) obiekt reprezentujący listę atrybutów niestandardowych; w przeciwnym razie zwraca wartość null, jeśli istnieją żadne atrybuty niestandardowe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub S_FALSE, jeśli istnieją żadne atrybuty niestandardowe dla tego pola. W przeciwnym razie zwraca kod błędu;

## <a name="remarks"></a>Uwagi
 Pole może mieć wiele atrybutów niestandardowych.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)