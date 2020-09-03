---
title: 'IDebugProgramHost2:: gethostname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722231"
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
