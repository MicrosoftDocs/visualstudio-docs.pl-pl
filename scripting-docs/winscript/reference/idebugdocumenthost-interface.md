---
title: Interfejs IDebugDocumentHost | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 46684bf2264813a8daaa466b98119496ba85d4b9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346543"
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