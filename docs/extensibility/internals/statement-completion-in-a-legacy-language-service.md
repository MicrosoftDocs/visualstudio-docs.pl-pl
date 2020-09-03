---
title: Uzupełnianie instrukcji w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704939"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Uzupełnianie instrukcji w starszej wersji usługi językowej
Uzupełnianie instrukcji to proces, za pomocą którego usługa języka ułatwia użytkownikom zakończenie słowa kluczowego języka lub elementu, który rozpoczął pisanie w edytorze podstawowym. W tym temacie opisano, jak działa uzupełnianie instrukcji i jak wdrożyć ją w usłudze językowej.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji uzupełniania instrukcji, zobacz [Przewodnik: wyświetlanie uzupełniania instrukcji](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="implementing-statement-completion"></a>Implementowanie uzupełniania instrukcji
 W edytorze podstawowym, uzupełnianie instrukcji aktywuje specjalny interfejs użytkownika, który interaktywnie ułatwia łatwiejsze i szybkie pisanie kodu. Uzupełnianie instrukcji ułatwia wyświetlanie odpowiednich obiektów lub klas, gdy są potrzebne, co pozwala uniknąć konieczności zapamiętywania określonych elementów lub konieczności ich wyszukiwania w temacie pomocy.

 Aby zaimplementować uzupełnianie instrukcji, język musi mieć wyzwalacz uzupełniania instrukcji, który można przeanalizować. Na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] używa operatora kropki (.), podczas gdy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] używa operatora strzałki (->). Usługa języka może używać więcej niż jednego wyzwalacza, aby inicjować uzupełnianie instrukcji. Te wyzwalacze są zaprogramowane w filtrze poleceń.

## <a name="command-filters-and-triggers"></a>Filtry poleceń i wyzwalacze
 Filtry poleceń przechwytuje wystąpienia wyzwalacza lub wyzwalacze. Aby dodać filtr polecenia do widoku, zaimplementuj <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i dołącz go do widoku przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Można użyć tego samego filtru poleceń ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) dla wszystkich aspektów usługi językowej, takich jak uzupełnianie instrukcji, znaczniki błędów i wskazówki dotyczące metod. Aby uzyskać więcej informacji, zobacz [przechwytywanie starszych poleceń usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Po wprowadzeniu wyzwalacza w edytorze — w odróżnieniu od buforu tekstu — usługa językowa następnie wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę. Powoduje to wyświetlenie przez Edytor interfejsu użytkownika, dzięki czemu użytkownik może wybrać spośród kandydatów uzupełniania instrukcji. Ta metoda wymaga implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag jako parametrów. Lista elementów ukończenia zostanie wyświetlona w przewijanym polu listy. Gdy użytkownik kontynuuje wpisywanie, wybór w polu listy zostanie zaktualizowany w celu odzwierciedlenia najbardziej pasujących do ostatnio wpisanych znaków. Podstawowy edytor implementuje interfejs użytkownika do uzupełniania instrukcji, ale usługa języka musi implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejs, aby zdefiniować zestaw elementów uzupełniających kandydatów dla instrukcji.

## <a name="see-also"></a>Zobacz też
- [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
