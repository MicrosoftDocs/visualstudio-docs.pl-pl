---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9ba7c7216c590f773f1054a1f06cd3412ff6b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796807"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs zapewnia dostęp do metody, która może utworzyć usługę wizualizatora, która jest używana do obsługi zadań wizualizatora typu dla środowiska IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs, aby utworzyć obiekt usługi wizualizatora, który z kolei służy do dostarczania identyfikatorów klasy `CLSID` wizualizatorów do środowiska IDE programu Visual Studio.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 W celu uzyskania tego interfejsu [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) ewaluatora wyrażeń (EE).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Tworzy usługę wizualizatora|  
  
## <a name="remarks"></a>Uwagi  
 `IEEVisualizerServiceProvider`Interfejs jest uzyskiwany podczas implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Usługa wizualizatora, którą tworzy ten interfejs, służy do dostarczania funkcji do interfejsu [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , który jest odpowiedzialny za wdrożenie. EE jest również odpowiedzialny za implementację interfejsu [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , który umożliwia wizualizatorom typów wyświetlanie i modyfikowanie wartości właściwości.  
  
 Zobacz [wizualizowanie i wyświetlanie danych,](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje na temat sposobu działania tych interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażeń](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
