---
title: Interfejs IDebugDocumentHelper | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7322ea5e2026ff3f4491ed1106dceb97a5f11c73
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58153464"
---
# <a name="idebugdocumenthelper-interface"></a>Interfejs IDebugDocumentHelper
Dostarczać implementacje dla wielu interfejsy niezbędne do obsługi inteligentne, takie jak `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, i `IDebugDocumentTextEvents` interfejsów.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugDocumentHelper` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Inicjuje pomocnika dokumentu debugowania z nazwą i początkowa atrybuty.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Dodaje ten dokument w drzewie dokumentu.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Usuwa ten dokument z drzewa dokumentu.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Dołącza ciąg Unicode do końca tego dokumentu.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Dołącza ciąg znaków Dwubajtowych do końca tego dokumentu.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Zestawy `IDebugDocumentHost` dla tego dokumentu.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Powiadamia pomocnika, że dany tekst jest dostępna, ale nie zawiera znaków.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Oznacza, że do elementu pomocniczego, będącego określonego zakresu znaków w bloku skryptu, obsługiwane przez aparat skryptu.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Ustawia atrybuty domyślnych dla tekstu, który nie znajduje się w bloku skryptu.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Ustawia atrybuty zakres tekstu.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Ustawia długa nazwa dokumentu.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Ustawia skróconą nazwę dokumentu.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Ustawia atrybuty dla tego dokumentu.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Zwraca węzeł aplikacji debugowania odpowiadającego do tego dokumentu.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Pobiera zakres znaków i aparat skryptów odpowiadający blok skryptu.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Tworzy nowy kontekst dokumentu debugowania.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Ten dokument udostępnia do góry w debugerze interfejsu użytkownika.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Udostępnia kontekst tego dokumentu do góry w interfejsie użytkownika debugera.|