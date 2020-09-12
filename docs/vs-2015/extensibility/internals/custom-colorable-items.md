---
title: Elementy niestandardowe z możliwością kolorowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24a4db907ec859c6075c06956f86939047379897
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "64795754"
---
# <a name="custom-colorable-items"></a>Niestandardowe elementy z możliwością kolorowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz przesłonić listę typów do kolorowania, na przykład słowa kluczowe i komentarze, implementując niestandardowe elementy do użycia w ramach usługi językowej.  
  
## <a name="user-settings-of-colorable-items"></a>Ustawienia użytkownika dla elementów z możliwością kolorowania  
 Możesz wyświetlić okno dialogowe **czcionki i kolory** , wybierając opcję **Opcje** w menu **Narzędzia** , a następnie wybierając **czcionkę i kolory** w obszarze **środowisko**. Po wybraniu ekranu, takiego jak **Edytor tekstu** lub **okno polecenia**, pole listy **Wyświetl elementy** pokazuje wszystkie elementy, które można kolorować dla tego ekranu. Można wyświetlić i zmienić czcionkę, rozmiar, kolor pierwszego planu i kolor tła dla każdego elementu, który można kolorować. Wybrane opcje są przechowywane w pamięci podręcznej w rejestrze i uzyskuje do nich dostęp za pomocą nazwy elementu, który można kolorować.  
  
## <a name="presentation-of-colorable-items"></a>Prezentacja elementów z możliwością kolorowania  
 Ze względu na to, że IDE obsługuje zastępowanie użytkowników elementów z możliwością kolorowania w oknie dialogowym **czcionki i kolory** , należy dostarczyć tylko każdy niestandardowy element z atrybutem z nazwą. Ta nazwa jest wyświetlana na liście **wyświetlanych elementów** . Elementy kolorowe są wyświetlane w kolejności alfabetycznej. Aby zgrupować niestandardowe elementy z kolorem, możesz rozpocząć każdą nazwę przy użyciu nazwy języka, na przykład **NewLanguage-Comment** i **NewLanguage-słowo kluczowe**.  
  
> [!CAUTION]
> Nazwa języka powinna być uwzględniona w nazwie elementu z możliwością kolorowania, aby uniknąć kolizji z istniejącymi nazwami elementów mających kolor. Jeśli zmienisz nazwę jednego z elementów z możliwością przykolorowania podczas tworzenia, musisz zresetować pamięć podręczną, która została utworzona przy pierwszym dostępie do elementów do przykolorowania. Eksperymentalną pamięć podręczną można zresetować za pomocą narzędzia CreateExpInstance, które jest instalowane razem z zestawem SDK programu Visual Studio, zazwyczaj w katalogu  
>   
> **C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
> Aby zresetować pamięć podręczną, wywołaj polecenie `CreateExpInstance /Reset` . Aby uzyskać więcej informacji na temat CreateExpInstance, zobacz [Narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Pierwszy element na liście elementów z możliwością kolorowania nigdy nie jest przywoływany. Pierwszy element odpowiada indeksowi elementu z kolorem 0 i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszym sposobem postępowania w przypadku tego elementu nie będącego w odwołaniu jest podawanie symbolu zastępczego elementu z możliwością uzyskania koloru na liście jako pierwszego elementu.  
  
## <a name="implementing-custom-colorable-items"></a>Implementowanie niestandardowych elementów z możliwością kolorowania  
  
1. Zdefiniuj, co ma być kolorowe w Twoim języku, na przykład słowo kluczowe, operator i identyfikator.  
  
2. Utwórz Wyliczenie tych elementów, które mają kolor.  
  
3. Skojarz typy tokenów zwrócone przez analizator lub skaner z wartościami wyliczanymi.  
  
    Na przykład wartości reprezentujące typy tokenów mogą być tymi samymi wartościami w wyliczeniu elementów niestandardowych.  
  
4. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> obiekcie Wypełnij listę atrybutów wartościami z wyliczenia niestandardowych elementów z możliwością przykolorowania odpowiadającą typom zwracanym z parsera lub skanera.  
  
5. W tej samej klasie, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejs i jego dwie metody, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
6. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7. Jeśli chcesz obsługiwać wartości 24-bitowe lub wysokie kolory, należy również zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejs.  
  
8. W obiekcie usługi językowej Utwórz listę zawierającą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> obiekty, jeden dla każdego elementu, który może być identyfikowany przez analizator lub skaner.  
  
    Możesz uzyskać dostęp do każdego elementu na liście przy użyciu odpowiadającej wartości z wyliczenia niestandardowych elementów z możliwością barwienia. Użyj wartości wyliczenia jako indeksu do listy. Pierwszy element na liście nigdy nie jest dostępny, ponieważ odnosi się do domyślnego stylu tekstu, który [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawsze obsługuje siebie. Można to skompensować, wstawiając symbol zastępczy na początku listy.  
  
9. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody Zwróć liczbę elementów na liście elementów niestandardowych, które można przykolorować.  
  
10. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody zwraca żądany element z możliwością kolorową z listy.  
  
    Przykład sposobu implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsów i można <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> znaleźć w temacie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .  
  
## <a name="see-also"></a>Zobacz też  
 [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
