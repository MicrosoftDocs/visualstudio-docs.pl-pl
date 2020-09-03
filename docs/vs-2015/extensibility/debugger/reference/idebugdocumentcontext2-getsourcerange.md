---
title: 'IDebugDocumentContext2:: GetSourceRange — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcec6af2b8e7b1acfdc9c3cf38cb18654be78c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145002"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera zakres kodu źródłowego tego kontekstu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBegPosition`  
 [in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana początkową pozycją. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.  
  
 `pEndPosition`  
 [in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana pozycją końcową. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres źródłowy to cały zakres kodu źródłowego od bieżącej instrukcji z powrotem do tuż po poprzedniej instrukcji, która przyczynia się do wykonania kodu. Zakres źródłowy jest zazwyczaj używany do mieszania instrukcji źródłowych, w tym komentarzy, z kodem w oknie demontażu.  
  
 Aby uzyskać zakres dla tylko instrukcji kodu zawartych w tym kontekście dokumentu, wywołaj metodę [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
