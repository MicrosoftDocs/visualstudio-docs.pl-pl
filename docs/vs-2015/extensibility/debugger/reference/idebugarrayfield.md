---
title: IDebugArrayField | Dokumentacja firmy Microsoft
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
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef60550dcea362fd196ba2740d7347981a6d01bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745635"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs w tym artykule opisano symbol tablicy lub typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu. Ten interfejs jest specjalizację, który reprezentuje tablicę obiektów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskać ten interfejs z [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_ARRAY`.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsów, ten interfejs wykonuje następujące czynności:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Pobiera liczbę elementów w tablicy.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Pobiera typ elementu w tablicy.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Pobiera rangę tablicy.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

