---
title: 'IDebugProgramHost2:: gethostname | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165126"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwType`  
 podczas Wartość z wyliczenia [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .  
  
 `pbstrHostName`  
 określoną Zwraca żądaną nazwę procesu hostingu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W typowej implementacji tej metody `dwType` parametr jest ignorowany i jest zwracana przyjazna nazwa komputera hosta. Kolejną możliwą implementacją jest przekazanie `dwType` parametru do wywołania metody [gethostname](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) w celu uzyskania nazwy.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
