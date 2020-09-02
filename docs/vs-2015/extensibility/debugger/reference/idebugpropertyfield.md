---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bad60a24c9120c1425a5d9041a32755feeb6e6c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692148"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs udostępnia funkcje, które umożliwiają pobieranie i Ustawianie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Ten interfejs jest specjalizacją, która obsługuje koncepcję właściwości klasy.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , aby uzyskać ten interfejs z interfejsu [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , jeśli metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca wartość `FIELD_KIND_PROP` .  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Oprócz metod w interfejsach [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Pobiera metodę, która pobiera właściwość.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Pobiera metodę, która ustawia właściwość.|  
  
## <a name="remarks"></a>Uwagi  
 Właściwość jest koncepcją kodu zarządzanego i reprezentuje metodę, która jest traktowana jako zmienna. Właściwości nie istnieją w niezarządzanym języku C++.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
