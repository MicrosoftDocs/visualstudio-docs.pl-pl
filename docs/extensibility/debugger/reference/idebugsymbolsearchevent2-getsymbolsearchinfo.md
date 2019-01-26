---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1eb6d2e22624744835275f69cb1eed0e212d659
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955446"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Metoda wywoływana przez program obsługi zdarzeń, aby pobrać wyniki dotyczące procesu ładowania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModule`  
 [out] Obiekt IDebugModule3 reprezentujący moduł, dla którego zostały załadowane symbole.  
  
 `pbstrDebugMessage`  
 [out w] Zwraca ciąg zawierający komunikaty o błędach z modułu. W przypadku braku błędów tego ciągu, po prostu będzie zawierać nazwę modułu, ale nigdy nie jest pusty.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` nie może być `NULL` i musi być zwolniona przez `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Kombinacja flag z [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Wyliczenie wskazujące, czy wszystkie symbole zostały załadowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po odebraniu program obsługi [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) zdarzeń po zostanie podjęta próba, aby załadować symbole debugowania dla modułu, program obsługi może wywołać ta metoda do określenia wyników tego obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)