---
title: Uzupełnianie zestawienia w starszej usłudze językowej | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704939"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Uzupełnianie instrukcji w starszej wersji usługi językowej
Uzupełnianie instrukcji jest procesem, w którym usługa języka pomaga użytkownikom zakończyć słowo kluczowe języka lub element, który rozpoczęli wpisywanie w edytorze podstawowym. W tym temacie omówiono, jak działa uzupełnianie instrukcji i jak zaimplementować go w usłudze języka.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowego sposobu implementowania uzupełniania instrukcji, zobacz [Przewodnik: Wyświetlanie uzupełniania instrukcji](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="implementing-statement-completion"></a>Realizacja instrukcji implementacji
 W edytorze core ukończenia instrukcji aktywuje specjalny interfejs użytkownika, który interaktywnie pomaga łatwiej i szybciej pisać kod. Uzupełnianie instrukcji pomaga, wyświetlając odpowiednie obiekty lub klasy, gdy są one potrzebne, co pozwala uniknąć konieczności zapamiętywania określonych elementów lub konieczności wyszukania ich w temacie odwołania pomocy.

 Aby zaimplementować ukończenie instrukcji, język musi mieć wyzwalacz ukończenia instrukcji, który może być analizowany. Na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] używa operatora kropki (.), [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] podczas gdy używa operatora strzałki (->). Usługa języka może używać więcej niż jednego wyzwalacza do inicjowania uzupełniania instrukcji. Wyzwalacze te są programowane w filtrze poleceń.

## <a name="command-filters-and-triggers"></a>Filtry poleceń i wyzwalacze
 Filtry poleceń przechwytują wystąpienia wyzwalacza lub wyzwalaczy. Aby dodać filtr poleceń do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> widoku, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> interfejs i dołącz go do widoku, wywołując metodę. Tego samego filtru poleceń (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) można użyć dla wszystkich aspektów usługi języka, takich jak uzupełnianie instrukcji, znaczniki błędów i porady dotyczące metod. Aby uzyskać więcej informacji, zobacz [Przechwytywanie poleceń usługi starszego języka](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Po wprowadzeniu wyzwalacza w edytorze — w szczególności buforu tekstu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> — usługa języka następnie wywołuje metodę. Powoduje to, że edytor do wywołania interfejsu użytkownika, dzięki czemu użytkownik może wybrać z kandydatów zakończenia instrukcji. Ta metoda wymaga <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> zaimplementowania i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flagi jako parametry. Lista elementów ukończenia pojawi się w przewijanym polu listy. W miarę jak użytkownik kontynuuje wpisywanie, zaznaczenie w polu listy jest aktualizowane w celu odzwierciedlenia najbliższego dopasowania do ostatnio wpisanych znaków. Edytor podstawowy implementuje interfejsu użytkownika do uzupełnienia instrukcji, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ale usługa języka musi implementować interfejs, aby zdefiniować zestaw elementów ukończenia kandydata dla instrukcji.

## <a name="see-also"></a>Zobacz też
- [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
