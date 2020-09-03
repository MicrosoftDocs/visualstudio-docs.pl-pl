---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190994"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera klasę, która należy do tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClassField`  
 określoną Zwraca obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) reprezentujący otaczającą klasę. Zwraca wartość null, jeśli nie ma żadnej klasy otaczającej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasa reprezentowana przez ten obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) jest klasą zagnieżdżoną, `ppClassField` parametr zwraca `IDebugClassField` obiekt reprezentujący otaczającą klasę. Na przykład, uwzględniając tę definicję klasy:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Wywołanie `GetEnclosingClass` metody na `IDebugClassField` obiekcie reprezentującym `NestedClass` klasę zwraca `IDebugClassField` obiekt reprezentujący klasę `RootClass` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
