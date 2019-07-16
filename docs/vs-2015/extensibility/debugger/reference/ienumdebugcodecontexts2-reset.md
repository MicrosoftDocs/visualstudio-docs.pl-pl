---
title: IEnumDebugCodeContexts2::Reset | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Reset
helpviewer_keywords:
- IEnumDebugCodeContexts2::Reset
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 284c8c4b50813fbdeb6decf4f1a9bd4b73a168e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158104"
---
# <a name="ienumdebugcodecontexts2reset"></a>IEnumDebugCodeContexts2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Resetuje wyliczenia do pierwszego elementu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po ta metoda jest wywoływana, następnym wywołaniu [dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md) metoda zwraca pierwszy element wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
