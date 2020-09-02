---
title: 'IDebugReference2:: setreferencetype | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31be7be2b9d17ca5b7af65e4d38668f88d484d9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178170"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ustawia typ referencyjny. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT SetReferenceType (   
   REFERENCE_TYPE dwRefType  
);  
```  
  
```csharp  
int SetReferenceType (   
   enum_REFERENCE_TYPE dwRefType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwRefType`  
 podczas Wartość z wyliczenia [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , która określa typ referencyjny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
