---
title: IDebugField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690304"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje pole, czyli opis symbolu lub typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs jako klasę bazową dla wszystkich pól.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest klasą bazową dla wszystkich pól. Na podstawie zwracanej wartości [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)ten interfejs może zwracać bardziej wyspecjalizowane interfejsy przy użyciu [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Ponadto wiele interfejsów zwraca `IDebugField` obiekty z różnych metod.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugField` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Pobiera informacje z informacji o symbolu lub typie.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Pobiera rodzaj pola.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Pobiera typ pola.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Pobiera kontener pola.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Pobiera adres pola.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Pobiera rozmiar pola w bajtach.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Pobiera rozszerzone informacje o polu.|  
|[Równe](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porównuje dwa pola.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Pobiera niezależne od typu informacje o symbolu lub typie.|  
  
## <a name="remarks"></a>Uwagi  
 Typ jest odpowiednikiem języka C `typedef` .  
  
 W poniższym przykładzie języka C++ `weather` jest typem klasy i `sunny` i `stormy` są symbolami:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Czy pole reprezentuje symbol czy typ można ustalić, wywołując metodę [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) i sprawdzając wynik [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Jeśli `FIELD_KIND_TYPE` bit jest ustawiony, pole jest typu, a jeśli `FIELD_KIND_SYMBOL` bit jest ustawiony, jest symbolem.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
