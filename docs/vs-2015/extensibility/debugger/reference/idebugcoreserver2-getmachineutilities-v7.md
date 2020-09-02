---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831177"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera narzędzia maszyny dla serwera.  
  
> [!NOTE]
> Ta metoda jest przestarzała: nie należy używać ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zawsze zwraca, `E_NOTIMPL` Jeśli ta metoda jest wywoływana). Jest on zachowywany z przyczyn historycznych.  
  
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
 określoną Zwraca `IDebugMDMUtil2_V7` interfejs, który reprezentuje informacje o narzędziu maszynowym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `E_NOTIMPL` , wskazując, że metoda nie jest zaimplementowana.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zawsze zwraca, `E_NOTIMPL` Jeśli ta metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
