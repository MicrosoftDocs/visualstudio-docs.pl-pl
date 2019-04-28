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
ms.openlocfilehash: 8e115c4e45784b2072bf626d90ebab0d980491e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871506"
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
