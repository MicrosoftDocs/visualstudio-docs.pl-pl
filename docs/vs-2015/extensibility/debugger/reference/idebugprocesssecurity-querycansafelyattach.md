---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 357ab447d0f16c3bbbfb656d042c0095df01bc83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784445"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda umożliwia dostawcy portu wyświetlić ostrzeżenie, zanim użytkownik dołącza do procesu niebezpieczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane są następujące:  
  
-   `S_OK`: Dołączanie do procesu jest bezpieczne, a okno dialogowe ostrzeżenia o nie jest wyświetlany.  
  
-   `S_FALSE`: Dołączanie może być problem z zabezpieczeniami i wyświetlane jest okno dialogowe z ostrzeżeniem.  
  
-   `FAILURE`: Dołączanie do procesu nie powiodło się.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

