---
title: IDebugEnumField | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c94b109ae29e40ead784cea565ad16c2a2b89d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794785"
---
# <a name="idebugenumfield"></a>IDebugEnumField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje typ wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs do reprezentowania wyliczenia.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskać ten interfejs z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_ENUM`.  
  
## <a name="methods-in-vtable-order"></a>Metody w VTable kolejności  
 Oprócz metod na `IDebugField` i `IDebugContainerField` interfejsów, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące nazwę dla tego typu wyliczeniowego.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Zwraca nazwę stała wyliczenia skojarzone z danej wartości.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Zwraca wartość skojarzoną z nazwa stałej wyliczenia danego|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Zwraca wartość skojarzoną z nazwą stała wyliczenia danego, ale bez uwzględnienia wielkości liter.|  
  
## <a name="remarks"></a>Uwagi  
 Jest podstawowym symbol, który faktycznie jest powiązane z lokalizacją z [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)
