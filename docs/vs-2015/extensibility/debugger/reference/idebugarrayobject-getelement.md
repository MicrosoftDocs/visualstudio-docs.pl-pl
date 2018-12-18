---
title: IDebugArrayObject::GetElement | Dokumentacja firmy Microsoft
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
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20da5d4770ecfe36fcb52e3609ee28be38491e84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764999"
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
 [in] Indeks elementu.  
  
 `ppElement`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejs, który reprezentuje element.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda uznaje wszystkie elementy obiektu tablicowego Jednowymiarowa tablica, nawet w przypadku obiektu tablicy wielowymiarowej. Na przykład, biorąc pod uwagę tablicy `myarray[3][2][6]` i `dwIndex` parametru 20, ta metoda zwróci element z `myarray[1][1][2]`, a `dwIndex` parametru 21 zwróci element z `myarray[1][1][3]`. Użyj [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodę, aby określić całkowitą liczbę elementów w tablicy.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

