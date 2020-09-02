---
title: 'IDebugField:: EQUAL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547315"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda porównuje to pole z określonym polem dla równości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pField`  
 podczas Pole, które ma zostać porównane z tym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli pola są takie same, zwraca `S_OK` . Jeśli pola są różne, zwraca `S_FALSE.` w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
