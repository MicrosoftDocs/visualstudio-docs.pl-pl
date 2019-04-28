---
title: Interfejs IDebugDocumentContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783197"
---
# <a name="idebugdocumentcontext-interface"></a>Interfejs IDebugDocumentContext
Udostępnia abstrakcyjną reprezentację w postaci części dokumentu debugowane. Taka reprezentacja dokumenty tekstowe składa się z pozycji znaku zakresu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugDocumentContext` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Zwraca dokument, który zawiera ten kontekst.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Wylicza kontekstów kodu skojarzone z tym kontekstem dokumentu.|