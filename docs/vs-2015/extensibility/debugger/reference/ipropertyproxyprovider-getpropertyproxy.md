---
title: 'IPropertyProxyProvider:: GetPropertyProxy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc505799a0ea7571ccff41057ba9852018ddbb3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199467"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera interfejs proxy właściwości dla podanego identyfikatora serwera proxy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwID`  
 podczas Identyfikator żądanego serwera proxy właściwości.  
  
 `proxy`  
 określoną Zwraca obiekt [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby zapewnić obsługę wizualizatorów typu zewnętrznego, ta metoda zwykle przekazuje wywołanie do metody [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) . Zobacz [wizualizowanie i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) , aby uzyskać szczegółowe informacje na temat sposobu uzyskiwania IEEVisualizerService.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
