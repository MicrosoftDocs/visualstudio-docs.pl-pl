---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca14e6236fc7e12ea259b97f7f2ddb69fe052f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692838"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs zapewnia dostęp do identyfikatora procesu, który jest właścicielem obiektu, którego adres jest reprezentowany przez ten interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Ten interfejs zapewnia dostęp do identyfikatora procesu, który jest właścicielem obiektu, który jest powiązany z tym adresem.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , aby uzyskać ten interfejs z interfejsu [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 Oprócz metod dziedziczonych z interfejsu [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Pobiera identyfikator procesu, który jest właścicielem obiektu reprezentowanego przez ten interfejs.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawcy symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
