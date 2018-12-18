---
title: Poleceń usługi w języka Legacy przechwytuje | Dokumentacja firmy Microsoft
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d89e2947cbd7bf1087f8dfa0ecffdd75033171
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752995"
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywanie poleceń starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], może mieć polecenia intercept usługi języka, które widoku tekstu w przeciwnym razie będzie obsługiwać. Jest to przydatne dla zachowania specyficzny dla języka, który nie zarządza widoku tekstu. Te polecenia mogą przechwycić, dodając co najmniej jeden filtr polecenia do widoku tekstu z usługi w języka.  
  
## <a name="getting-and-routing-the-command"></a>Routing poleceń i wprowadzenie  
 Filtr polecenia jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt, który monitoruje niektórych sekwencje znaków lub klucza poleceń. Można skojarzyć więcej niż jeden filtr polecenia przy użyciu widoku w jeden tekst. Każdy widok tekstu zachowuje filtry służbowej. Po utworzeniu nowego filtru polecenia Dodaj filtr do łańcucha dla widoku odpowiedni tekst.  
  
 Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> można dodać filtr poleceń w łańcuchu. Gdy wywołujesz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zwraca inny filtr polecenia, do którego można przekazać poleceń, które nie obsługuje polecenia filtru.  
  
 Masz następujące opcje obsługi polecenia:  
  
- Obsługa polecenia, a następnie przekaż polecenia do następnego filtru poleceń w łańcuchu.  
  
- Obsługa polecenia i nie są przekazywane do polecenia do następnego filtru polecenia.  
  
- Nie obsługują polecenia, ale ona przekazać polecenie do następnego filtru polecenia.  
  
- Ignoruj polecenia. Nie obsługują w bieżący filtr, a nie są przekazywane do następnego filtru.  
  
  Aby uzyskać informacje dotyczące polecenia powinna obsługiwać usługi w języka, zobacz [ważne polecenia dotyczące filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).

