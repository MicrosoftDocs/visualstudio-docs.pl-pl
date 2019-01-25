---
title: IDebugMethodField::EnumAllLocals | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833757"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy moduł wyliczający dla wszystkich zmiennych lokalnych, metody, włącznie z wygenerowanymi przez kompilator wewnętrznie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt reprezentujący adres debugowania, w metodzie wskazujące określonym zakresie lub kontekście.  
  
 `ppLocals`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę wszystkich zmiennych lokalnych w określonym zakresie; w przeciwnym razie zwraca wartość null wskazującą nie zmiennych lokalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wyliczane są tylko zmienne zdefiniowane w obrębie bloku, który zawiera adres danego debugowania. Ta metoda obejmuje zmienne lokalne generowanych przez kompilator. Jeśli wszystkie, które jest wymagane są lokalne jawnie zdefiniowane w źródle, wywołanie [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) metody.  
  
 Metoda może zawierać wielu kontekstach lub bloków zakresu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
