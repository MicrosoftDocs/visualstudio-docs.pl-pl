---
title: IDebugBinder3 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f23c2ad4aeaf911e45b28686584d741e5c4d22f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704137"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs zapewnia dostęp do typów, aliasów i usług niestandardowego wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs do obsługi aliasów, niestandardowego wizualizatora usług i dostęp do informacji o typie obiektu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu uzyskuje ten interfejs, za pomocą [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod dostarczonych przez [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu, ten interfejs wykonuje następujące czynności:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Pobiera obiekt pamięci reprezentująca pamięci, z którym powiązany jest ten obiekt.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Pobiera wyjątek skojarzone z tym obiektem (jeśli istnieje)|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Pobiera nadać jej nazwę aliasu|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Pobiera tablicę wszystkie aliasy dla tego obiektu|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Pobiera liczbę typów argumentów skojarzonych z tym obiektem|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Pobiera listę typów argumentów skojarzonych z tym obiektem|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Pobiera interfejs do niej wizualizatora|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konwertuje lokalizacji obiektu lub adresów pamięci 64-bitowych w kontekście pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
