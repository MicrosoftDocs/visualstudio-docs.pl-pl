---
title: IDebugMethodField::GetThis | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 786f3986875518470ed5756a0f7b57f4f93f5ca2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804970"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera `this` (`Me` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) wskaźnik obiekt zawierający metodę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClass`  
 [out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentujący "to" wskaźnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W językach obiektowych jest zazwyczaj dorozumianych wskaźnik do bieżącego wystąpienia klasy. Jest to nazywane `this` w języku C# / C++ i `Me` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
