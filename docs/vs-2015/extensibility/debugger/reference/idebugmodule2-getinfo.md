---
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 476ffb2901dfe6a8d09ca707fc47089f4d99d97d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162499"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera informacje o tym module.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 podczas Kombinacja flag z wyliczenia [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) , która określa, które pola `pInfo` mają być wypełnione.  
  
 `pInfo`  
 [in. out] Struktura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , która jest wypełniana opisem modułu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Struktura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) zawiera nazwę modułu, który jest wyświetlany w oknie **moduły** .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
