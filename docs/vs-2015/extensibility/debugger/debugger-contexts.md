---
title: Konteksty debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 771a3cd8ae25173f3033b3a3229e516570f5dedc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200632"
---
# <a name="debugger-contexts"></a>Konteksty debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowaniu aparat debugowania (de) działa jednocześnie w kilku odrębnych kontekstach w następujący sposób:  
  
- Kontekst kodu, który opisuje bieżącą lokalizację w strumieniu wykonywania programu.  
  
- Kontekst lub pozycja dokumentacji, która opisuje bieżące położenie w dokumencie źródłowym.  
  
- Kontekst oceny wyrażenia, który opisuje kontekst, w którym będą wykonywane obliczenia wyrażeń.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)  
 Omawia kontekst kodu jako adres w strumieniu instrukcji programu w dzisiejszych architekturach czasu wykonywania i nietradycyjnych językach, gdzie kod nie może być reprezentowany przez instrukcje, ale inne sposoby.  
  
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)  
 Definiuje położenie dokumentu w debugowaniu w programie Visual Studio za pomocą abstrakcji pozycji w pliku źródłowym, jak znany IDE.  
  
 [Kontekst dokumentu](../../extensibility/debugger/document-context.md)  
 Omówienie kontekstu dokumentu reprezentowanego w debugowaniu programu Visual Studio w odniesieniu do pliku źródłowego. Omówiono również sposób mapowania kontekstu kodu do kontekstu dokumentacji przez program obsługi symboli.  
  
 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
 Zawiera informacje o kontekście oceny wyrażenia w programie Visual Studio. Na przykład kontekst oceny wyrażenia skojarzonego z ramką stosu zawiera kontekst do oceny zmiennych lokalnych, parametrów metody i elementów członkowskich klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Koncepcje debugowania](../../extensibility/debugger/debugger-concepts.md)  
 Opisuje główne koncepcje dotyczące architektury debugowania.  
  
 [Składniki debugowania](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), ewaluatora wyrażeń (EE) i obsługę symboli (SH).  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera linki do różnych zadań debugowania, takich jak uruchamianie programu i ocenianie wyrażeń.
