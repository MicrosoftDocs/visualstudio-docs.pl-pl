---
title: Uzupełnianie instrukcji w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723217"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Uzupełnianie instrukcji w starszej wersji usługi językowej
Uzupełnianie instrukcji to proces, za pomocą którego usługa języka ułatwia użytkownikom zakończenie słowa kluczowego języka lub elementu, który rozpoczął pisanie w edytorze podstawowym. W tym temacie opisano, jak działa uzupełnianie instrukcji i jak wdrożyć ją w usłudze językowej.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji uzupełniania instrukcji, zobacz [Przewodnik: wyświetlanie uzupełniania instrukcji](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="implementing-statement-completion"></a>Implementowanie uzupełniania instrukcji
 W edytorze podstawowym, uzupełnianie instrukcji aktywuje specjalny interfejs użytkownika, który interaktywnie ułatwia łatwiejsze i szybkie pisanie kodu. Uzupełnianie instrukcji ułatwia wyświetlanie odpowiednich obiektów lub klas, gdy są potrzebne, co pozwala uniknąć konieczności zapamiętywania określonych elementów lub konieczności ich wyszukiwania w temacie pomocy.

 Aby zaimplementować uzupełnianie instrukcji, język musi mieć wyzwalacz uzupełniania instrukcji, który można przeanalizować. Na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] używa operatora kropki (.), podczas gdy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] używa operatora strzałkowego (->). Usługa języka może używać więcej niż jednego wyzwalacza, aby inicjować uzupełnianie instrukcji. Te wyzwalacze są zaprogramowane w filtrze poleceń.

## <a name="command-filters-and-triggers"></a>Filtry poleceń i wyzwalacze
 Filtry poleceń przechwytuje wystąpienia wyzwalacza lub wyzwalacze. Aby dodać filtr polecenia do widoku, zaimplementuj interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> i dołącz go do widoku, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Można użyć tego samego filtru poleceń (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) dla wszystkich aspektów usługi językowej, takich jak uzupełnianie instrukcji, znaczniki błędów i wskazówki dotyczące metody. Aby uzyskać więcej informacji, zobacz [przechwytywanie starszych poleceń usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Po wprowadzeniu wyzwalacza w edytorze — w odróżnieniu od buforu tekstu — usługa językowa następnie wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>. Powoduje to wyświetlenie przez Edytor interfejsu użytkownika, dzięki czemu użytkownik może wybrać spośród kandydatów uzupełniania instrukcji. Ta metoda wymaga implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> i flag <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> jako parametrów. Lista elementów ukończenia zostanie wyświetlona w przewijanym polu listy. Gdy użytkownik kontynuuje wpisywanie, wybór w polu listy zostanie zaktualizowany w celu odzwierciedlenia najbardziej pasujących do ostatnio wpisanych znaków. Podstawowy edytor implementuje interfejs użytkownika do uzupełniania instrukcji, ale usługa języka musi zaimplementować interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>, aby zdefiniować zestaw elementów uzupełniających kandydatów dla instrukcji.

## <a name="see-also"></a>Zobacz także
- [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)