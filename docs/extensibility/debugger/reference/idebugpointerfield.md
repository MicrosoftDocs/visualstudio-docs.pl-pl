---
title: IDebugPointerField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fc686af78b4ac787abef1c0c52309e82c47376b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947897"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Ten interfejs reprezentuje typ wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs do reprezentacji wskaźnika.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na `IDebugField` i `IDebugContainerField` interfejsów, ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisującej cel wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 W języku C/C++ wskaźnik może mieć kontener, jeśli jest on używany w tablicy notacji. Na przykład, biorąc pod uwagę `char *pString`, `pString` ma typ wskaźnika do `char`. `pString[3]` Typ kontenera, który jest wskaźnikiem do `char` odwołujący się czwarty element tego kontenera.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)