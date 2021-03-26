---
description: Pobiera identyfikator dla domeny aplikacji.
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1caec6968f9a67a15a31c8064b7795a37a6829
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059109"
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
