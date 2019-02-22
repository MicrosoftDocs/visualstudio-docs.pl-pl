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
ms.openlocfilehash: 9b7b0aa54cb5102867ba536729404ad298db9fd3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678179"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Ta metoda pobiera narzędzia komputera dla serwera.

> [!NOTE]
>  Ta metoda jest przestarzała: nie używaj ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana). Jest zachowane ze względów historycznych.

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

#### <a name="parameters"></a>Parametry
 `ppUtil`

 [out] Zwraca `IDebugMDMUtil2_V7` interfejs, który reprezentuje dane narzędzia maszyny.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`, wskazujący, że metoda nie jest zaimplementowana.

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)