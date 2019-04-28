---
title: Interfejs IDebugDocumentHost | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939228"
---
# <a name="idebugdocumenthost-interface"></a>Interfejs IDebugDocumentHost
Uwidacznia funkcje specyficzne dla hosta, takie jak kolorowania do debugera. `IDebugDocumentHelper::SetDebugDocumentHost` Metoda przyjmuje ten interfejs jako argument.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugDocumentHost` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Zwraca szeroką gamę znaków, które zostały dodane za pomocą `IDebugDocumentHelper::AddDeferredText`, w oryginalnym dokumencie hosta.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Zwraca atrybuty tekst w bloku tekstu dokumentu.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Powiadamia hosta, jest tworzony nowy kontekst dokumentu i Zezwalaj hostowi na opcjonalnie zwracać obiekt, który kontroluje nowy kontekst.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Zwraca pełną ścieżkę (łącznie z nazwą pliku) pliku źródłowego dokumentu.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Zwraca nazwę dokumentu, bez informacji o ścieżce.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Powiadamia hosta, zapisania pliku źródłowego dokumentu i jego zawartość powinna być odświeżane.|