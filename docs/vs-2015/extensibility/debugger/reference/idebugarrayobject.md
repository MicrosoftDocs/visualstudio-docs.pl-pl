---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f8ec4c883078663d0e252d6a04ae7441f12f31d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686987"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje obiekt Array.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować tablicę.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) może uzyskać ten interfejs przy użyciu [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , jeśli obiekt reprezentuje tablicę.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Oprócz metod w `IDebugObject` interfejsie, w interfejsie są zaimplementowane następujące metody `IDebugArrayObject` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Pobiera liczbę elementów w tablicy.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Pobiera element tablicy.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Pobiera wszystkie elementy tablicy.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Pobiera rangę tablicy.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Pobiera Wymiary tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluatora wyrażeń używa tego interfejsu do reprezentowania tablic w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: EE. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
