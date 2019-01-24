---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67ab8a7343cd320470515b757dfca905a0a4690e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786733"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera interfejs kodu zarządzanego, który reprezentuje wartość skojarzoną z tego aliasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppUnk`  
 [out] `IUnknown` interfejs, który reprezentuje wartość skojarzoną z tego aliasu. Ten interfejs może być odpytywany dla `ICorDebugValue` interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ma zastosowanie tylko do zarządzanych wartości ( `ICorDebugValue` jest dostępny w interfejsie [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] i jest definiowany w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawu SDK w pliku cordebug.idl).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
