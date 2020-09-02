---
title: 'IDebugSymbolSearchEvent2:: GetSymbolSearchInfo — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8ef097ed02ae90b03289e3a2f3a1ad3f0ad8618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788152"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wywoływane przez procedurę obsługi zdarzeń w celu pobrania wyników procesu ładowania symboli.  
  
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
 określoną Obiekt IDebugModule3 reprezentujący moduł, dla którego zostały załadowane symbole.  
  
 `pbstrDebugMessage`  
 [in. out] Zwraca ciąg zawierający wszystkie komunikaty o błędach z modułu. Jeśli nie ma żadnych błędów, ten ciąg będzie zawierać nazwę modułu, ale nigdy nie jest pusty.  
  
> [!NOTE]
> [C++] `pbstrDebugMessage` nie może być `NULL` i musi być zwolniona z `SysFreeString` .  
  
 `pdwModuleInfoFlags`  
 określoną Kombinacja flag z wyliczenia [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) wskazująca, czy zostały załadowane wszystkie symbole.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy program obsługi odbiera zdarzenie [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) po wykonaniu próby załadowania symboli debugowania dla modułu, program obsługi może wywołać thismethod, aby określić wyniki tego obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
