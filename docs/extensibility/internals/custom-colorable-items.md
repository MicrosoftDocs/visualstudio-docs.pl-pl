---
title: Niestandardowe elementy do barwienia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708993"
---
# <a name="custom-colorable-items"></a>Niestandardowe elementy nadajne kolorami
Listę typów do kolorowania, takich jak słowa kluczowe i komentarze, można zastąpić, implementując niestandardowe elementy colorable jako część usługi językowej.

## <a name="user-settings-of-colorable-items"></a>Ustawienia użytkownika elementów colorable
 Okno **dialogowe Czcionki i kolory** można wyświetlić, wybierając polecenie **Opcje** w menu **Narzędzia,** a następnie wybierając pozycję **Czcionki i kolory** w obszarze **Środowisko**. Po wybraniu wyświetlania, takiego jak **Edytor tekstu** lub **Okno polecenia,** na liście **Elementy wyświetlane** są wszystkie elementy barwne dla tego ekranu. Dla każdego elementu barwnego można wyświetlać i zmieniać czcionkę, rozmiar, kolor pierwszego planu i kolor tła. Opcje są przechowywane w pamięci podręcznej w rejestrze i dostępne przez kolorowalną nazwę elementu.

## <a name="presentation-of-colorable-items"></a>Prezentacja elementów kolorowych
 Ponieważ IDE obsługuje zastąpienia użytkowników elementów colorable w oknie dialogowym **Czcionki i kolory,** należy podać tylko każdy niestandardowy element colorable z nazwą. Ta nazwa jest wyświetlana na liście **Elementy wyświetlane.** Kolorowe elementy są wyświetlane w kolejności alfabetycznej. Aby zgrupować niestandardowe elementy kolorysty usługi językowej, możesz rozpocząć każdą nazwę od nazwy języka, na przykład **NewLanguage - Comment** i **NewLanguage - Keyword**.

> [!CAUTION]
> Należy dołączyć nazwę języka w nazwie elementu colorable, aby uniknąć kolizji z istniejącymi nazwami elementów colorable. Jeśli zmienisz nazwę jednego z elementów colorable podczas tworzenia, należy zresetować pamięć podręczną, która została utworzona po raz pierwszy elementy colorable były dostępne. Eksperymentalną pamięć podręczną można zresetować za pomocą narzędzia **CreateExpInstance,** które jest instalowane przy pomocy zestawu SDK programu Visual Studio, zazwyczaj w katalogu:
>
> *C:\Pliki programu (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Aby zresetować pamięć podręczną, wprowadź **createExpInstance /Reset**. Aby uzyskać więcej informacji na temat **createexpinstance**, zobacz [CreateExpInstance narzędzie](../../extensibility/internals/createexpinstance-utility.md).

 Pierwszy element na liście elementów colorable nigdy nie odwołuje. Pierwszy element odpowiada indeksowi elementu colorable 0 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i zawsze dostarcza domyślne kolory i atrybuty tekstu dla tego elementu. Najprostszym sposobem radzenia sobie z tym elementem bez odwołań jest dostarczenie elementu zastępczego colorable na liście jako pierwszy element.

## <a name="implement-custom-colorable-items"></a>Implementowanie niestandardowych elementów colorable

1. Zdefiniuj, co musi być pokolorowane w twoim języku, na przykład słowo kluczowe, operator i identyfikator.

2. Utwórz wyliczenie tych elementów colorable.

3. Skojarz typy tokenów zwrócone z analizatora lub skanera z wyliczonymi wartościami.

    Na przykład wartości reprezentujące typy tokenów mogą być takie same wartości w niestandardowe elementy colorable wyliczenia.

4. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> obiekcie wypełnij listę atrybutów wartościami z niestandardowego wyliczenia elementów colorable odpowiadających typom tokenów zwróconych z analizatora lub skanera.

5. W tej samej klasie, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> która <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> implementuje interfejs, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> zaimplementuj interfejs i jego dwie metody oraz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

6. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Jeśli chcesz obsługiwać 24-bitowe lub wysokie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> wartości kolorów, należy również zaimplementować interfejs.

8. W obiekcie usługi języka utwórz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> listę zawierającą obiekty, po jednej dla każdego elementu, który można zidentyfikować w przypadku poszczególnych kolorów, który można zidentyfikować.

    Dostęp do każdego elementu na liście można uzyskać przy użyciu odpowiedniej wartości z niestandardowego wyliczenia elementów colorable. Użyj wartości wyliczenia jako indeksu na liście. Pierwszy element na liście nigdy nie jest dostępny, ponieważ odpowiada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] domyślnemu stylowi tekstu, który zawsze się obsługuje. Można to zrekompensować, wstawiając element zastępczy colorable na początku listy.

9. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody zwróć liczbę elementów na liście elementów niestandardowych elementów colorable.

10. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody zwróć żądany element colorable z listy.

    Na przykład jak zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsy, zobacz .

## <a name="see-also"></a>Zobacz też
- [Model starszej usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)
- [Jak: Używanie wbudowanych elementów kolorowych](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
