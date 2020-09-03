---
title: 'IDebugFunctionObject:: xmlarrayobject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205810"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy obiekt Array. Ta tablica może zawierać wartości pierwotne lub wystąpienia obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ot`  
 podczas Określa wartość z wyliczenia [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) wskazującego typ nowego obiektu tablicy.  
  
 `pClassField`  
 podczas Obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący klasę obiektu, jeśli tworzysz tablicę wartości wystąpienia obiektu. Jeśli tworzysz tablicę obiektów pierwotnych, ten parametr jest wartością null.  
  
 `dwRank`  
 podczas Ranga lub liczba wymiarów tablicy.  
  
 `dwDims`  
 podczas Rozmiary każdego wymiaru tablicy.  
  
 `dwLowBounds`  
 podczas Początek każdego wymiaru (zwykle 0 lub 1).  
  
 `ppObject`  
 określoną Zwraca obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzoną tablicę. Jest to obiekt [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje parametr Array do funkcji reprezentowanej przez interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
