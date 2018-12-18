---
title: IEEVisualizerDataProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 844f591055eb309be3ff14171d937b2998d47c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724090"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs zapewnia możliwość zmiany wartość obiektu za pomocą Wizualizator typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs do modyfikowania danych w obiekcie właściwości, za pośrednictwem Wizualizator typów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest używany do tworzenia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) obiektu za pomocą wywołania [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać więcej informacji.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Określa, czy jest to możliwe zaktualizować obiekt (i następnie jego wartość) reprezentujących ten Wizualizator.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Wymusza ponownej oceny obiektu dla tej wizualizatora.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Pobiera istniejący obiekt ten Wizualizator (nie oceny odbywa się).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualizuje obiekt ten Wizualizator, zmieniając wartość, która przedstawia wizualizatora.|  
  
## <a name="remarks"></a>Uwagi  
 Usługa visualizer (reprezentowane przez [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfejs i zwrócony przez [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) przechowuje odwołania do obiektu implementującego `IEEVisualizerDataProvider` interfejsu . W rezultacie `IEEVisualizerDataProvider` interfejsu nie powinny zostać wdrożone na tym samym obiekcie, który implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Jeśli ten obiekt przechowuje odwołania do `IEEVisualizerService` obiektu: wyniki odwołanie cykliczne i Zakleszczenie występuje, gdy obiekty są niszczone. Zalecanym podejściem jest implementacja `IEEVisualizerDataProvider` na oddzielnym obiektem, do którego `IDebugProperty2` obiektu delegatów bez wywoływania `IUnknown::AddRef` na nim.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)

