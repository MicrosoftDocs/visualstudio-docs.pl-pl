---
title: Przechwycenie poleceń starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195012"
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywanie poleceń starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] możesz mieć polecenia przechwycenia usługi językowej, które w przeciwnym razie mógłby obsłużyć widok tekstu. Jest to przydatne w przypadku zachowania specyficznego dla języka, które nie jest zarządzane przez widok tekstu. Te polecenia można przechwycić, dodając jeden lub więcej filtrów poleceń do widoku tekstu z usługi językowej.  
  
## <a name="getting-and-routing-the-command"></a>Pobieranie i kierowanie polecenia  
 Filtr polecenia jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektem, który monitoruje pewne sekwencje znaków lub polecenia kluczowe. Można skojarzyć więcej niż jeden filtr poleceń z pojedynczym widokiem tekstu. Każdy widok tekstu zachowuje łańcuch filtrów poleceń. Po utworzeniu nowego filtru poleceń należy dodać filtr do łańcucha dla odpowiedniego widoku tekstu.  
  
 Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> celu dodania filtru poleceń do łańcucha. Po wywołaniu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zwraca inny filtr polecenia, do którego można przekazać polecenia, których filtr polecenia nie obsługuje.  
  
 Dostępne są następujące opcje obsługi poleceń:  
  
- Obsłuż polecenie, a następnie Przekaż polecenie do następnego filtru poleceń w łańcuchu.  
  
- Obsłuż polecenie i nie przekazuj polecenia do następnego filtru poleceń.  
  
- Nie obsługuj polecenia, ale Przekaż polecenie do następnego filtru poleceń.  
  
- Zignoruj polecenie. Nie obsługuj go w bieżącym filtrze i nie przekazuj go do następnego filtru.  
  
  Aby uzyskać informacje o poleceniach, które powinny być obsługiwane przez usługę języka, zobacz [Ważne polecenia dla filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).
