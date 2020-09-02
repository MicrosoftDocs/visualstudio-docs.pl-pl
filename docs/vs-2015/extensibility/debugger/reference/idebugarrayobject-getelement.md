---
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423689"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera element tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 podczas Indeks elementu.  
  
 `ppElement`  
 określoną Zwraca interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , który reprezentuje element.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda widzi wszystkie elementy obiektu Array jako tablicę jednowymiarową, nawet jeśli obiekt Array jest wielowymiarowych. Na przykład, dana tablica `myarray[3][2][6]` i `dwIndex` parametr 20, ta metoda zwróci element z `myarray[1][1][2]` , a `dwIndex` parametr 21 zwróci element z `myarray[1][1][3]` . Użyj metody [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) , aby określić łączną liczbę elementów w tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
