---
title: Przechwytywanie starszych poleceń usługi językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707448"
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywanie poleceń starszej wersji usługi językowej
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]programze można mieć polecenia przechwytywania usługi języka, które w przeciwnym razie obsłużyłyby widok tekstu. Jest to przydatne w przypadku zachowania specyficznego dla języka, które nie zarządza widokiem tekstu. Można przechwycić te polecenia, dodając jeden lub więcej filtrów poleceń do widoku tekstowego z usługi językowej.

## <a name="getting-and-routing-the-command"></a>Uzyskiwanie i wyznaczanie polecenia
 Filtr poleceń <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jest obiektem monitorujcyjne sekwencje znaków lub polecenia klawiszy. Można skojarzyć więcej niż jeden filtr poleceń z jednym widokiem tekstowym. Każdy widok tekstu zachowuje łańcuch filtrów poleceń. Po utworzeniu nowego filtru poleceń należy dodać filtr do łańcucha dla odpowiedniego widoku tekstu.

 Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na, aby dodać filtr poleceń do łańcucha. Po <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>wywołaniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwraca inny filtr poleceń, do którego można przekazać polecenia, których filtr poleceń nie obsługuje.

 Dostępne są następujące opcje obsługi poleceń:

- Obsłuż polecenie, a następnie przekaż polecenie do następnego filtru poleceń w łańcuchu.

- Obsłuż polecenie i nie przekazuje polecenia do następnego filtru poleceń.

- Nie należy obsługiwać polecenia, ale przekazać polecenie do następnego filtru polecenia.

- Zignoruj polecenie. Nie należy obsługiwać go w bieżącym filtrze i nie przekazywać go do następnego filtru.

  Aby uzyskać informacje o tym, które polecenia powinna obsługiwać usługa językowa, zobacz [Ważne polecenia filtrów usług językowych](../../extensibility/internals/important-commands-for-language-service-filters.md).
