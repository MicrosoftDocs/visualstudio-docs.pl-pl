---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a13c7a868234098059539c8221aefab2e168a459
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802600"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy wystąpienie pola, biorąc pod uwagę tablicę argumentów typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cArgs`  
 [in] Liczba argumentów w `ppArgs` tablicy.  
  
 `ppArgs`  
 [in] Tablica, która zawiera argumenty typu. Argumenty typu muszą być zamknięte typy (Ogólne nieogólnego lub w pełni utworzona).  
  
 `ppConstructedField`  
 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejs, który reprezentuje nowe pole.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ograniczenia nie są sprawdzane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

