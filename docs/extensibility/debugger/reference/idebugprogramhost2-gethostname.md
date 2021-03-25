---
description: Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.
title: 'IDebugProgramHost2:: gethostname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53b4d69be1ea24f5c240b6247539f499c9fb00fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084015"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parametry
`dwType`\
podczas Wartość z wyliczenia [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .

`pbstrHostName`\
określoną Zwraca żądaną nazwę procesu hostingu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W typowej implementacji tej metody `dwType` parametr jest ignorowany i jest zwracana przyjazna nazwa komputera hosta. Kolejną możliwą implementacją jest przekazanie `dwType` parametru do wywołania metody [gethostname](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) w celu uzyskania nazwy.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
