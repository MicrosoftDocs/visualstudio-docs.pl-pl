---
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c50473e12399e3977de55e67c7251d5783eecfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947128"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Pobiera identyfikator dla domeny aplikacji.

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
określoną Zwraca identyfikator domeny aplikacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Identyfikator domeny aplikacji zmienia się za każdym razem, gdy aplikacja zostanie ponownie uruchomiona i zostanie utworzona nowa domena aplikacji.

## <a name="see-also"></a>Zobacz też
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
