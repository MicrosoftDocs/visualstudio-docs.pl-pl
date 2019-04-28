---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445292"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera narzędzia komputera dla serwera.  
  
> [!NOTE]
> Ta metoda jest przestarzała: nie używaj ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana). Jest zachowane ze względów historycznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zawsze zwraca `E_NOTIMPL` Jeśli ta metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
