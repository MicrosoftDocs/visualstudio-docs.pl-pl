---
description: Ta metoda pobiera narzędzia maszyny dla serwera.
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc58f41d9cca98f6c15c164ed4acb941345627e5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154772"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Ta metoda pobiera narzędzia maszyny dla serwera.

> [!NOTE]
> Ta metoda jest przestarzała: nie należy używać ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca, `E_NOTIMPL` Jeśli ta metoda jest wywoływana). Jest on zachowywany z przyczyn historycznych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametry
`ppUtil`\
określoną Zwraca `IDebugMDMUtil2_V7` interfejs, który reprezentuje informacje o narzędziu maszynowym.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL` , wskazując, że metoda nie jest zaimplementowana.

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca, `E_NOTIMPL` Jeśli ta metoda jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
