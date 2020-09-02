---
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4b4b17242d1d2098c085acae0b88c91ecfb5441
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547757"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera informacje, które są w stanie wyświetlić.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 podczas Kombinacja stałych [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) , które wybierają informacje do wyświetlenia. Jeśli pole reprezentuje symbol, zazwyczaj jest to nazwa symbolu i typ.  
  
 `pFieldInfo`  
 określoną Zwraca informacje w podanej strukturze [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
