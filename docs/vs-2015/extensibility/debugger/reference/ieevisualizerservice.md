---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3bb741aa25cf6695f1dd1d8d66fc0c1846413b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64798508"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs implementuje podstawowe metody, które dostarczają funkcje do interfejsów [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) i [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs, aby umożliwić ewaluatora wyrażeń (EE) obsługę wizualizatorów typów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 EE dzwoni do [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) w celu uzyskania tego interfejsu jako części obsługi wizualizatorów typów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Pobiera liczbę niestandardowych podglądów, o których wie ta usługa.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Pobiera listę niestandardowych osób przeglądających.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Zwraca obiekt proxy dla właściwości.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Pobiera liczbę ciągów wartości do wyświetlenia dla określonej właściwości lub pola.|  
  
## <a name="remarks"></a>Uwagi  
 IDE używa interfejsu [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , aby ustalić, czy istnieją jakieś niestandardowe przeglądarki lub Wizualizatory typu dla właściwości. Tworząc usługę wizualizatora (z [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), EE mogą oferować funkcje `IDebugProperty3` i [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (obsługujące wyświetlanie i zmienianie interfejsów wartości właściwości), a tym samym obsługę wizualizatorów typów.  
  
 Jeśli EE zawiera niestandardowe przeglądające, które same implementują, EE mogą dołączać `CLSID` te niestandardowe osoby do końca listy zwróconej przez [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Dzięki temu do obsługi programów do wizualizacji typów i własnych, niestandardowych osób przeglądających. Upewnij się, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla dodanie jakichkolwiek niestandardowych osób przeglądających.  
  
 Zobacz [wizualizator typów i Podgląd niestandardowy](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) w celu omówienia różnic między wizualizatorami i osobami przeglądających.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażeń](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
