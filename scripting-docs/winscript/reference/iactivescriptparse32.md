---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347648"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Jeśli skrypt Windows aparat pozwala nieprzetworzony tekst skryptlety kodu do dodania do skryptu lub zezwala na tekst wyrażenie oceniane w czasie wykonywania, implementuje `IActiveScriptParse32` interfejsu. Dla interpretowanych języków skryptów, które mają nie niezależnych środowisko tworzenia, np. VBScript, zapewnia to alternatywny mechanizm (inne niż `IPersist*`) pobierać kod skryptu do silnika wykonywania skryptów i Dołącz fragmenty skryptu do różnych obiektów zdarzenia.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Dodaje skryptletu kodu do skryptu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicjuje aparat skryptów.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizuje danego skryptletu kodu, dodając deklaracje do przestrzeni nazw i oceniając kod, zgodnie z potrzebami.|