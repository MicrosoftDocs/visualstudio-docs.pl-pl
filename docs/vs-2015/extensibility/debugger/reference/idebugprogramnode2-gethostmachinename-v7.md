---
title: IDebugProgramNode2::GetHostMachineName_V7 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f3c8d43e0186ff368494d65a681ded58ef7f2bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765942"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrHostMachineName`  
 [out] Zwraca nazwę komputera, w którym jest uruchomiony program.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja zawsze powinna zwrócić `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
>  Począwszy od programu [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

