---
title: IDebugPointerObject::D ereference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40a0e66e5f3cb3a50618a3c8dd4fd5926c34c624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201009"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera obiekt wskazywany przez.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 podczas Proste przesunięcie bajtów od początku obiektu wskazywanego przez.  
  
 `ppObject`  
 określoną Zwraca obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący obiekt wskazywany, a także przesunięcie, jeśli istnieje.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten obiekt nie wskazuje innego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wskazywany może być typem pierwotnym lub bardziej złożonym, takim jak Klasa lub struktura.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
