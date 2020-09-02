---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20d5df8df3e556f0908668b98a836cbedbbce47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687007"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs opisuje symbol lub typ tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Ten interfejs jest specjalizacją reprezentującą obiekty tablicowe.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , aby uzyskać ten interfejs z interfejsu [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_ARRAY` .  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Oprócz metod w interfejsach [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące elementy:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Pobiera liczbę elementów w tablicy.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Pobiera typ elementu w tablicy.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Pobiera rangę tablicy.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
