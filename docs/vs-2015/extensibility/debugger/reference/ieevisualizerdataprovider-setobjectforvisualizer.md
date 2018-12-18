---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Dokumentacja firmy Microsoft
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
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d5a939bbb14fa820811fc2f40907cb635aa9027
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751699"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda zmienia obiekt, który reprezentuje wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pNewObject`  
 [in] Obiekt, który można ustawić.  
  
 `error`  
 [out] Jeśli wystąpił błąd podczas ustawiania obiektu, ten ciąg zawiera komunikat o błędzie.  
  
 `pException`  
 [out] Jeśli wystąpił błąd, ten obiekt przechowuje informacje o wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jest implementujący, aby określić, jak informacje o błędzie jest zwracana. Jednak jest możliwe, że niektóre obiekty wywołujące mogą tylko wygląd, aby zobaczyć, jeśli obiekt wyjątku został zwrócony wiedzieć, był błąd, więc ta metoda zawsze powinna zwracać obiekt wyjątku, jeśli wystąpił błąd. W przypadku, gdy obiekt wywołujący chce mieć należy również dostarczyć ciąg błędu z niego korzystać.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

