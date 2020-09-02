---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d7f6fc12a3366200ca1e14c0e2d55f4f6d797f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694351"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

W tym interfejsie opisano metodę.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Ten interfejs jest specjalizacją, która przedstawia metodę.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , aby uzyskać ten interfejs z interfejsu [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , jeśli zwraca wartość [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_METHOD` . Ponadto metody, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)i [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), zwracają `IDebugMethodField` interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Oprócz metod w interfejsach [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Tworzy moduł wyliczający dla parametrów metody.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Pobiera wskaźnik "This" obiektu zawierającego metodę.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Tworzy moduł wyliczający dla wszystkich zmiennych lokalnych metody.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Tworzy moduł wyliczający dla wybranych zmiennych lokalnych metody.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Określa, czy określony atrybut niestandardowy został zdefiniowany.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Tworzy moduł wyliczający dla statycznych zmiennych lokalnych metody.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Pobiera kontener globalny metody.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Tworzy moduł wyliczający dla typu każdego argumentu wymaganego do wywołania metody.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda może zawierać parametry, a także zmienne lokalne.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
