---
title: IDebugField | Dokumentacja firmy Microsoft
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
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4feaec188bcfcfbca9f6484e162f1c3e6ad22d67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764977"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje pole, oznacza to, że opis symboli lub typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs jako klasa bazowa dla wszystkich pól.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest klasą bazową dla wszystkich pól. Na podstawie wartości zwracanej z [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), ten interfejs może zwracać bardziej wyspecjalizowane interfejsy przy użyciu [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Ponadto zwrócić wiele interfejsów `IDebugField` obiektów z różnych metod.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugField`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Pobiera zawiera informacje dotyczące symboli lub typu.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Pobiera rodzaj pola.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Pobiera typ pola.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Pobiera kontener pola.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Pobiera adres tego pola.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Pobiera rozmiar pola, w bajtach.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Pobiera rozszerzone informacje dotyczące pola.|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porównuje dwa pola.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Pobiera niezależnie od typu informacji na temat symboli lub typu.|  
  
## <a name="remarks"></a>Uwagi  
 Typ jest odpowiednikiem języka C `typedef`.  
  
 W poniższym przykładzie języka C++ `weather` jest typem klasy i `sunny` i `stormy` są symbolami:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Czy pole reprezentuje symbolu, lub można określić typu przez wywołanie metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) i sprawdzając [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) wynik. Jeśli `FIELD_KIND_TYPE` ustawiony bit, pole jest typem Jeśli `FIELD_KIND_SYMBOL` ustawiony bit, jest symbolem.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

