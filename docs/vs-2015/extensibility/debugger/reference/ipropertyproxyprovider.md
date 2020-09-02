---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700045"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs dostarcza interfejs proxy do wyświetlania i zmieniania danych obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluatora wyrażeń służy do implementowania tego interfejsu w tym samym obiekcie, który implementuje interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) w ramach pomocy technicznej EE dla wizualizatorów typu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj metodę [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugProperty3` interfejsie, aby uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 `IPropertyProxyProvider`Interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Pobiera interfejs proxy właściwości w celu wyświetlenia danych w obiekcie.|  
  
## <a name="remarks"></a>Uwagi  
 Chociaż usługa EE implementuje ten interfejs, implementacja [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) jest zwykle obsługiwana przez [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Zobacz [wizualizowanie i wyświetlanie danych,](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje na temat uzyskiwania interfejsu IEEVisualizerService.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Wizualizator typów i Podgląd niestandardowy](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
