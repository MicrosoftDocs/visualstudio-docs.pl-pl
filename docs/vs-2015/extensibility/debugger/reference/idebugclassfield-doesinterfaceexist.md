---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f71346c1b69729ae54ef0d33be4149e7000316c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779896"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, jeśli określony interfejs jest zdefiniowana w klasie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszInterfaceName`  
 [in] Ciąg zawierający nazwę interfejsu do wyszukania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK, zwraca wartość S_FALSE, jeśli nie ma interfejsu; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obowiązuje pobiera wyliczenie wszystkich interfejsów i wyszukuje listę zgodnych interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
