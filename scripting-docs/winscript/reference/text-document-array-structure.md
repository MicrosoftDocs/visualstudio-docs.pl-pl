---
title: Struktura TEXT_DOCUMENT_ARRAY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d188729b68f8086da62d40ca28fc29945c8be7f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152239"
---
# <a name="textdocumentarray-structure"></a>Struktura TEXT_DOCUMENT_ARRAY
Tablica [interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md) obiektów. Elementy członkowskie są przydzielane przy użyciu CoTaskMemAlloc.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwCount`  
 Liczba dokumentów.  
  
 `Members`  
 Zestaw dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)