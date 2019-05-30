---
title: IDebugAlias2::GetAppDomainId | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40d52c5eedf0defb845f1944acd166d48dca1ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338174"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Pobiera identyfikator domeny aplikacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parametry
`pappDomainId`\
[out] Zwraca identyfikator domeny aplikacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zmiany identyfikatora domeny aplikacji przy każdym ponownym uruchomieniu aplikacji i nowej domeny aplikacji jest tworzona.

## <a name="see-also"></a>Zobacz także
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)