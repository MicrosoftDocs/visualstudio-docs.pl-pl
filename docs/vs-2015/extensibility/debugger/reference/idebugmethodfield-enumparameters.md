---
title: 'IDebugMethodField:: EnumParameters | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ebdd604ba97fda8751cf037e7494b59e7bb77ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162598"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy moduł wyliczający dla parametrów metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę parametrów do metody; w przeciwnym razie zwraca wartość null, jeśli nie ma parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma parametrów. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element jest obiektem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentującym różne typy parametrów. Wywołaj metodę [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) dla każdego obiektu, aby określić, jakiego rodzaju parametru reprezentuje ten obiekt.  
  
 Parametr zawiera zarówno nazwę zmiennej, jak i jej typ. Pierwszym parametrem metody klasy jest zwykle wskaźnik "This".  
  
 Jeśli potrzebujesz tylko typów parametrów, wywołaj metodę [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
