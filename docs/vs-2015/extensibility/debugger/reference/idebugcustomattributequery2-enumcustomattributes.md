---
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b09285b2fbab65321d0949be7fbd9c7a03c54ed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568411"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera moduł wyliczający dla wszystkich atrybutów niestandardowych dołączonych do tego pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Zwraca obiekt [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) reprezentujący listę atrybutów niestandardowych; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych atrybutów niestandardowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca S_OK lub S_FALSE, jeśli nie ma żadnych atrybutów niestandardowych tego pola. W przeciwnym razie zwraca kod błędu;  
  
## <a name="remarks"></a>Uwagi  
 Pole może mieć wiele atrybutów niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
