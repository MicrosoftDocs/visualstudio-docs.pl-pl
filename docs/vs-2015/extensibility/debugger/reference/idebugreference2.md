---
title: IDebugReference2 | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438967"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje odwołanie do właściwości ramki stosu lub niektóre inne właściwości.  
  
> [!NOTE]
> `IDebugReference2` jest zarezerwowany do użytku w przyszłości i wszystkie jego metody powinna zwrócić `E_NOTIMPL`.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do reprezentowania odwołanie do konkretnego typu wartości. Na przykład wartość można wartość liczbową, w wyniku oceny wyrażenia kontekstu pamięci, służący do wyświetlania w pamięci lub Podaj listę rejestrów i ich wartości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [getreference —](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) uzyskać ten interfejs. [Getparent —](../../../extensibility/debugger/reference/idebugreference2-getparent.md) i [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) również zwracać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugReference2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Pobiera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strukturę, która opisuje to odwołanie.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Ustawia wartość tego odwołania z ciągu.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Ustawia wartość odwołanie z innego odwołania.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Wylicza elementy podrzędne tego odwołania.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Pobiera element nadrzędny tego odwołania.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Pobiera odniesienie najbardziej pochodnego tego odwołania.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Pobiera bajtów pamięci, do których odnosi się to odwołanie.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Pobiera kontekst pamięci dla tego odwołania.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Pobiera rozmiar w bajtach, to odwołanie.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Ustawienie tego typu odwołania.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Porównuje to odwołanie z inną.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> To wykorzystania "property" nie należy mylić z tej zmiennej składowej klasy, co oznacza, mimo że `IDebugReference2` może reprezentować podmiot.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentuje właściwość, podczas gdy `IDebugReference2` reprezentuje odwołanie do właściwości, zwykle odwołanie do obiektu w debugowanego programu.  
  
 Główna różnica między właściwością i odwołania jest, że właściwość odwołuje się do nazwanego wystąpienia obiektu, gdy odwołanie odnosi się do nazwy wystąpienia. Na przykład właściwość może odwoływać się do obiektu w stosie tego programu przez `"a.b"`. Inna właściwość może odwoływać się do tego samego obiektu jako `"c.d"`. Sposób odwoływania się do tej właściwości wymaga, aby `"a.b"` lub `"c.d"` się mieścić w zakresie. Odwołanie do tego samego obiektu nie została określona; obiekt może zostać udzielona tak długo, jak pamięć dla tego obiektu jest prawidłowa.  
  
 `IDebugProperty2` Interfejsu można traktować jako wartość składającą się z nazwy, typu i adres. `IDebugReference2`, Z drugiej strony drugiej strony, można traktować jako typ i adresu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
