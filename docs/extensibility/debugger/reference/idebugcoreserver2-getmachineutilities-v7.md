---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0aff4ccea937536530d74dde13a5ba8a7b14bca7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205668"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Ta metoda pobiera narzędzia komputera dla serwera.

> [!NOTE]
> Ta metoda jest przestarzała: nie używaj ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana). Jest zachowane ze względów historycznych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametry
`ppUtil`\
[out] Zwraca `IDebugMDMUtil2_V7` interfejs, który reprezentuje dane narzędzia maszyny.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`, wskazujący, że metoda nie jest zaimplementowana.

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)