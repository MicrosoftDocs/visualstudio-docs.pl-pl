---
title: IDebugAlias2::GetAppDomainId | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 890e215c7e575e67a4360717851bab538966f419
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715053"
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

#### <a name="parameters"></a>Parametry
 `pappDomainId`

 [out] Zwraca identyfikator domeny aplikacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zmiany identyfikatora domeny aplikacji przy każdym ponownym uruchomieniu aplikacji i nowej domeny aplikacji jest tworzona.

## <a name="see-also"></a>Zobacz też
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)