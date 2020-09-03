---
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07dac3f407b6869dad90f06d778911fdd9cfed41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724872"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Ustawia dostawcę usług.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Parametry
`pSP`\
podczas Odwołanie do interfejsu dostawcy usług.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda zostanie wywołana przed wywołaniem jakichkolwiek innych metod.

## <a name="see-also"></a>Zobacz też
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
