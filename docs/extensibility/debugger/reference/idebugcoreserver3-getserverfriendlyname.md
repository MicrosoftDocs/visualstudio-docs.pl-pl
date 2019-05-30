---
title: IDebugCoreServer3::GetServerFriendlyName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba0675038a495a91755794d7e43ad57cfc7d438a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326953"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Pobiera przyjazną nazwę dla serwera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametry
`pbstrName`\
[out] Zwraca przyjazną nazwę dla serwera.

> [!NOTE]
> Obiekt wywołujący jest odpowiedzialny za zwalnianie ciągu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku serwerów uruchomione przez użytkownika nazwę zwracanego przez tę metodę jest pełna nazwa serwera. Dla serwerów z uruchamiany automatycznie nazwa to, że na komputerze serwera jest uruchomiona na.

 Dla nazwy zorientowane na komputerze, należy wywołać [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)