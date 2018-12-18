---
title: IDebugManagedObject::GetManagedObject | Dokumentacja firmy Microsoft
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
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 583a62b98d29f1be7626443cd2e1b069cf388d5c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770774"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca interfejs, który reprezentuje obiektu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppManagedObject`  
 [out] Zwraca interfejs, który reprezentuje obiektu zarządzanego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs zwrócone w wyniku tej metody można wykonywać zapytania, dla dowolnego interfejsu implementowany przez klasy zarządzanej, dzięki czemu jego metody do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

