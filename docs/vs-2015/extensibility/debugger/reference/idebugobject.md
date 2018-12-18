---
title: IDebugObject | Dokumentacja firmy Microsoft
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
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67db4808b8f20ea759ad5847508307e9efff5620
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785692"
---
# <a name="idebugobject"></a>IDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje obiekt, który tworzy obiekt wiążący, do hermetyzacji wartości symboli i wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluatora wyrażeń implementuje ten interfejs reprezentujący obiekt.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest klasą bazową dla wszystkich obiektów używanych przez ewaluatora wyrażeń w wyrażeniach przeanalizowany. Jest on zwracany przez wywołanie [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md) metody. [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskuje bardziej wyspecjalizowane interfejsy, w tym interfejsie.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugObject`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Pobiera rozmiar obiektu.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Pobiera wartość obiektu jako serię kolejnych bajtów.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Ustawia wartość obiektu z kolejnych serię bajtów.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Ustawia wartość odwołanie do tego obiektu.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Pobiera kontekst pamięci, która reprezentuje adres wartość obiektu.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Tworzy kopię obiektu zarządzanego w przestrzeni adresowej aparatu debugowania.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Sprawdza, czy ten obiekt jest odwołanie o wartości null.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porównuje obiekt do wskazanego.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Określa, czy ten obiekt tylko do odczytu.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Określa, czy obiekt przezroczystym serwerem proxy.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluator wyrażeń używa tego interfejsu jako klasę bazową do reprezentowania obiektów w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Getelement —](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)

