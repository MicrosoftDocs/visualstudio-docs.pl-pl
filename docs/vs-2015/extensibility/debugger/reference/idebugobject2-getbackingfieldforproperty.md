---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536389"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera pole lub zmienną (jeśli istnieje), która może tworzyć kopię zapasową Właściwości reprezentowanej przez ten obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 określoną Obiekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) opisujący pole zapasowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) reprezentuje właściwość klasy kodu zarządzanego, czyli metodę z akcesorem get i/lub Set. Takie właściwości zwykle wymagają zmiennej, aby zawierała wartość manipulowaną przez właściwość. Ta zmienna jest znana jako pole zapasowe. Jeśli nie ma pola zapasowego dla obiektu, upewnij się, że zwracana jest wartość null: niektóre obiekty wywołujące mogą nie zwracać uwagi na wartość zwracaną, ale zamiast tego sprawdzają, czy wartość null została zwrócona w `ppObject` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
