---
title: Interfejs IDebugDocumentText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 763678b08c22fe34ec6ffebbe670fb8b50af6576
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344398"
---
# <a name="idebugdocumenttext-interface"></a>Interfejs IDebugDocumentText
Zapewnia dostęp do wersji tylko do tekstu dokumentu debugowania. Ten interfejs obowiązują następujące zasady:  
  
- Pozycje znaku i numery wierszy są zera.  
  
- Pozycje znaku reprezentują znaków offsetowych; nie reprezentują bajtów lub word przesunięcia. W przypadku systemu Win32 pozycja znaku jest przesunięcie Unicode.  
  
  Oprócz metod odziedziczone `IDebugDocument`, `IDebugDocumentText` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Zwraca atrybuty dokumentu.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Zwraca liczbę wierszy i liczbę znaków w dokumencie.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Zwraca wartość pozycji znaku odpowiadający pierwszego znaku wiersza.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odnosi się do danej pozycji znaku.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Pobiera znaki i/lub atrybuty znaków skojarzonych z zakresem pozycji znaku.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Zwraca zakres pozycji znaku odpowiadający kontekstu dokumentu.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Tworzy obiekt kontekstu dokumentu odpowiadający zakres pozycji podana znaków.|