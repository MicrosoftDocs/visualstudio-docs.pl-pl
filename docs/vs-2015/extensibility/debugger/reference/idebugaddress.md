---
title: IDebugAddress | Dokumentacja firmy Microsoft
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
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82c532434475a46a6bf13a5b2395d6db1799cc15
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743993"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje adres elementu. Jest zwracany przez program obsługi symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs reprezentujący adres obiektu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wiele metod w wielu interfejsach zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Pobiera [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury opisujący obiekt i jego lokalizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Dostawca symboli zwraca ten interfejs reprezentujący obiekt i jego lokalizacji w ramach określonego zakresu (na przykład, funkcji, metody lub klasy). Ten interfejs jest zwracana z i przekazywane do różnych metod dostawca symboli i wyrażenie ewaluatora. Zazwyczaj dostawca symboli jest tylko jednostki, która wymaga nterpretowanie zawartości tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

