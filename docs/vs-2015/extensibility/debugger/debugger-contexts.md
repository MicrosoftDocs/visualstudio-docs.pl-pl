---
title: Konteksty debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b39e53ab06d3ce1633a77fc1fe324206f144dda1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793545"
---
# <a name="debugger-contexts"></a>Konteksty debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania, aparat debugowania (DE) działa jednocześnie w ramach kilku różnych kontekstach, w następujący sposób:  
  
-   Kontekst kodu w tym artykule opisano bieżącej lokalizacji w usłudze stream wykonywania programu.  
  
-   Dokumentacja kontekstu lub pozycji, który opisuje bieżącą pozycję w dokumencie źródłowym.  
  
-   Kontekst oceny wyrażeń, który opisuje kontekst, w wyrażeniu, które odbędzie się oceny.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)  
 W tym artykule omówiono kontekst kodu jako adresu program strumień instrukcji w współczesnych środowiska wykonawczego architektury i nietradycyjnych języków, gdzie kod nie może być reprezentowany przez instrukcje, ale w inny sposób.  
  
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)  
 Definiuje położenie dokumentu w programie Visual Studio debugowania za pomocą abstrakcję pozycji w pliku źródłowym, ponieważ wiadomo, że środowisko IDE.  
  
 [Kontekst dokumentu](../../extensibility/debugger/document-context.md)  
 W tym artykule omówiono jakie kontekstu dokumentu reprezentuje podczas debugowania programu Visual Studio w odniesieniu do pliku źródłowego. Omówiono również sposób obsługi symboli mapowania kontekst kodu do kontekstu dokumentacji.  
  
 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
 Zawiera informacje dotyczące oceny wyrażenia kontekstu w programie Visual Studio. Na przykład oceny wyrażenia kontekstu skojarzonego z ramką stosu udostępnia kontekst dla ocenianie zmiennych lokalnych, parametrów metod i składowych klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugowania](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
 [Składniki debugowania](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i wyrażeń.

