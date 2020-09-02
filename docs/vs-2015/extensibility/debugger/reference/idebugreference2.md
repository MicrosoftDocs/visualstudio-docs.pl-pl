---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785188"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje odwołanie do właściwości ramki stosu lub innej właściwości.  
  
> [!NOTE]
> `IDebugReference2` jest zarezerwowany do użytku w przyszłości, a wszystkie jej metody powinny zwrócić `E_NOTIMPL` .  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, aby reprezentować odwołanie do określonego rodzaju wartości. Na przykład wartość może być wartością liczbową w wyniku obliczenia wyrażenia, kontekstu pamięci używanego do wyświetlania pamięci lub listy rejestrów i ich wartości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj metodę [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) , aby uzyskać ten interfejs. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) i [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) zwracają również ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugReference2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Pobiera strukturę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , która opisuje to odwołanie.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Ustawia wartość tego odwołania z ciągu.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Ustawia wartość tego odwołania z innego odwołania.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Wylicza elementy podrzędne tego odwołania.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Pobiera element nadrzędny tego odwołania.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Pobiera najbardziej pochodne odwołanie do tego odwołania.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Pobiera bajty pamięci, do których odwołuje się to odwołanie.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Pobiera kontekst pamięci dla tego odwołania.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Pobiera rozmiar (w bajtach) tego odwołania.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Ustawia ten typ odwołania.|  
|[Porównaj](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porównuje to odwołanie z innym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Tego zastosowania właściwości "Property" nie należy mylić z tym, że oznacza zmienną składową klasy, chociaż `IDebugReference2` może reprezentować taką jednostkę.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentuje właściwość, podczas gdy `IDebugReference2` reprezentuje odwołanie do właściwości, zazwyczaj odwołanie do obiektu w debugowanym programie.  
  
 Główna różnica między właściwością a odwołaniem polega na tym, że Właściwość odwołuje się do nazwanego wystąpienia obiektu, podczas gdy odwołanie odwołuje się do nienazwanego wystąpienia. Na przykład właściwość może odwoływać się do obiektu w stercie programu przez `"a.b"` . Inna właściwość może odwoływać się do tego samego obiektu co `"c.d"` . Sposób odwoływania się do tej właściwości wymaga, aby `"a.b"` lub `"c.d"` znajdować się w zakresie. Odwołanie do tego samego obiektu jest pustego; Obiekt może być określony tak długo, jak pamięć dla tego obiektu jest prawidłowa.  
  
 `IDebugProperty2`Interfejs może być uważany za wartość o nazwie, typie i adresie. Z `IDebugReference2` drugiej strony, można traktować jako typ i adres.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
