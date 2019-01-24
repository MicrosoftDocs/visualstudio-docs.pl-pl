---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762940"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zostanie wyświetlone okno dialogowe określonego, który umożliwia użytkownikowi wybranie portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hwndParentDialog`  
 [in] Dojście do nadrzędnego okna dialogowego.  
  
 `pbstrPortId`  
 [out] Ciąg identyfikatora portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwracana wartość wynosząca `S_FALSE` (lub wartości zwracanej przez `S_OK` z `BSTR` równa `NULL`) wskazuje, że użytkownik kliknął **anulować**.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
