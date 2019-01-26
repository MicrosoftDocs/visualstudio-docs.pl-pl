---
title: Poleceń usługi w języka Legacy przechwytuje | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bb888e83f10d887c15b9ebf9fd67acad28f8e4c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037762"
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywanie poleceń starszej wersji usługi językowej
Za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], może mieć polecenia intercept usługi języka, które widoku tekstu w przeciwnym razie będzie obsługiwać. Jest to przydatne dla zachowania specyficzny dla języka, który nie zarządza widoku tekstu. Te polecenia mogą przechwycić, dodając co najmniej jeden filtr polecenia do widoku tekstu z usługi w języka.  
  
## <a name="getting-and-routing-the-command"></a>Routing poleceń i wprowadzenie  
 Filtr polecenia jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt, który monitoruje niektórych sekwencje znaków lub klucza poleceń. Można skojarzyć więcej niż jeden filtr polecenia przy użyciu widoku w jeden tekst. Każdy widok tekstu zachowuje filtry służbowej. Po utworzeniu nowego filtru polecenia Dodaj filtr do łańcucha dla widoku odpowiedni tekst.  
  
 Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> można dodać filtr poleceń w łańcuchu. Gdy wywołujesz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwraca inny filtr polecenia, do którego można przekazać poleceń, które nie obsługuje polecenia filtru.  
  
 Masz następujące opcje obsługi polecenia:  
  
- Obsługa polecenia, a następnie przekaż polecenia do następnego filtru poleceń w łańcuchu.  
  
- Obsługa polecenia i nie są przekazywane do polecenia do następnego filtru polecenia.  
  
- Nie obsługują polecenia, ale ona przekazać polecenie do następnego filtru polecenia.  
  
- Ignoruj polecenia. Nie obsługują w bieżący filtr, a nie są przekazywane do następnego filtru.  
  
  Aby uzyskać informacje dotyczące polecenia powinna obsługiwać usługi w języka, zobacz [ważne polecenia dotyczące filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).