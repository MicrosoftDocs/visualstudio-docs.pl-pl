---
title: IDebugExtendedField::IsClosedType | Dokumentacja firmy Microsoft
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
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 372a9acd274de1a20470bb7dfa50bc7d41a0ce00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808365"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, czy pole reprezentuje zamkniętego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to pole jest zamkniętego typu, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

