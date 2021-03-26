---
title: Przechwycenie poleceń starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak używać filtrów poleceń w programie Visual Studio, aby przechwycić starsze polecenia usługi językowej i dodać zachowanie specyficzne dla języka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d7af9ff4a8f04382cff4999b8c57549f3da3db7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074694"
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywanie poleceń starszej wersji usługi językowej
Za pomocą programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] możesz mieć polecenia przechwycenia usługi językowej, które w przeciwnym razie mógłby obsłużyć widok tekstu. Jest to przydatne w przypadku zachowania specyficznego dla języka, które nie jest zarządzane przez widok tekstu. Te polecenia można przechwycić, dodając jeden lub więcej filtrów poleceń do widoku tekstu z usługi językowej.

## <a name="getting-and-routing-the-command"></a>Pobieranie i kierowanie polecenia
 Filtr polecenia jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektem, który monitoruje pewne sekwencje znaków lub polecenia kluczowe. Można skojarzyć więcej niż jeden filtr poleceń z pojedynczym widokiem tekstu. Każdy widok tekstu zachowuje łańcuch filtrów poleceń. Po utworzeniu nowego filtru poleceń należy dodać filtr do łańcucha dla odpowiedniego widoku tekstu.

 Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> celu dodania filtru poleceń do łańcucha. Po wywołaniu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwraca inny filtr polecenia, do którego można przekazać polecenia, których filtr polecenia nie obsługuje.

 Dostępne są następujące opcje obsługi poleceń:

- Obsłuż polecenie, a następnie Przekaż polecenie do następnego filtru poleceń w łańcuchu.

- Obsłuż polecenie i nie przekazuj polecenia do następnego filtru poleceń.

- Nie obsługuj polecenia, ale Przekaż polecenie do następnego filtru poleceń.

- Zignoruj polecenie. Nie obsługuj go w bieżącym filtrze i nie przekazuj go do następnego filtru.

  Aby uzyskać informacje o poleceniach, które powinny być obsługiwane przez usługę języka, zobacz [Ważne polecenia dla filtrów usługi językowej](../../extensibility/internals/important-commands-for-language-service-filters.md).
