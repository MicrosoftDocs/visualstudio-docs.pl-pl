---
title: Niestandardowe elementy z możliwością kolorowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5777c5bf6340ac25888bf4a8446c61a68757c6fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989755"
---
# <a name="custom-colorable-items"></a>Niestandardowe elementy z możliwością kolorowania
Lista typów można zastąpić dla kolorowanie, takich jak słowa kluczowe i komentarze, implementując niestandardowe elementy z możliwością kolorowania jako część usługi języka.  
  
## <a name="user-settings-of-colorable-items"></a>Ustawienia użytkownika elementów z możliwością kolorowania  
 Możesz wyświetlić **czcionki i kolory** okno dialogowe, wybierając **opcje** na **narzędzia** menu, a następnie wybierając **czcionki i kolory** w obszarze **środowiska**. Po wybraniu ekranu, takich jak **edytora tekstów** lub **okna polecenia**, **wyświetlania elementów** pole listy przedstawia wszystkie elementy z możliwością kolorowania, obok którego wyświetlona. Można wyświetlić i zmienić czcionkę, rozmiar, kolor pierwszego planu i kolor tła dla każdego elementu z możliwością kolorowania. Wybrane opcje są przechowywane w pamięci podręcznej w rejestrze i dostępne według nazwy elementu z możliwością kolorowania.  
  
## <a name="presentation-of-colorable-items"></a>Prezentacja elementów z możliwością kolorowania  
 Ponieważ IDE obsługuje napisanie użytkownika elementów z możliwością kolorowania **czcionki i kolory** okno dialogowe, należy tylko podać każdego elementu z możliwością kolorowania niestandardowego o nazwie. Ta nazwa jest wyświetlana w **wyświetlania elementów** listy. Elementy z możliwością kolorowania są wyświetlane w kolejności alfabetycznej. Aby zgrupować niestandardowe elementy z możliwością kolorowania usługi języka, możesz rozpocząć nazwy z Twoją nazwą języka na przykład **NewLanguage — komentarz** i **NewLanguage — słowo kluczowe**.  
  
> [!CAUTION]
>  Nazwa języka należy uwzględnić w nazwie elementu z możliwością kolorowania, aby uniknąć konfliktów z już istniejącymi nazwami elementów z możliwością kolorowania. Jeśli zmienisz nazwę jednego z elementów z możliwością kolorowania podczas projektowania należy zresetować pamięć podręczną, która została utworzona po raz pierwszy uzyskano elementów z możliwością kolorowania. Możesz zresetować eksperymentalne pamięci podręcznej przy użyciu **CreateExpInstance** narzędzia, które jest instalowany z programem Visual Studio SDK, zwykle znajduje się w katalogu:  
>   
>  *C:\Program pliki (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>   
>  Aby zresetować pamięć podręczną, należy wprowadzić **/reset CreateExpInstance**. Aby uzyskać więcej informacji na temat **CreateExpInstance**, zobacz [narzędzie CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Nigdy nie odwołuje się do pierwszego elementu na liście elementów z możliwością kolorowania. Pierwszy element odnosi się do elementu z możliwością kolorowania indeksu 0, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszy sposób radzenia sobie z tym elementem nieużywanej jest umożliwiają określanie wartości elementu z możliwością kolorowania symbolu zastępczego na liście jako pierwszy element.  
  
## <a name="implement-custom-colorable-items"></a>Implementowanie niestandardowych elementów z możliwością kolorowania  
  
1. Zdefiniuj, co musi być w trybie kolorowym w swoim języku, na przykład — słowo kluczowe, Operator i identyfikator.  
  
2. Utwórz wyliczenie z tych elementów z możliwością kolorowania.  
  
3. Skojarz typy tokenów zwrócone przez analizator i skaner z wartości wyliczenia.  
  
    Na przykład wartości reprezentujących typy tokenów, może być takie same wartości w wyliczeniu niestandardowe elementy z możliwością kolorowania.  
  
4. W danej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> method in Class metoda swoje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> obiektu, należy wypełnić listę atrybutów przy użyciu wartości z wyliczenia swoje niestandardowe elementy z możliwością kolorowania, odpowiadające typy tokenów zwrócone przez analizator i skaner.  
  
5. W tej samej klasy, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu, implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu i jego dwóch metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu.  
  
7. Jeśli chcesz obsługiwać kolor 24-bitowego lub o wysokiej wartości, również zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu.  
  
8. W obiekt usługi języka, Utwórz listę zawierającą Twoje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> obiektów, po jednym dla każdego elementu z możliwością kolorowania zidentyfikuje skanera lub analizatora.  
  
    Przy użyciu odpowiedniej wartości z wyliczenia niestandardowe elementy z możliwością kolorowania można uzyskać dostęp do każdego elementu na liście. Użyj wartości wyliczenia jako indeks do listy. Pierwszy element na liście nigdy nie jest dostępne, ponieważ odnosi się do tekstu domyślnego stylu, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawsze obsługuje sam. Można zniwelować to przez wstawienie elementu z możliwością kolorowania symbolu zastępczego na początku listy.  
  
9. W danej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody zwracają liczbę elementów na liście niestandardowych elementów z możliwością kolorowania.  
  
10. W danej implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody zwracają żądanego elementu z możliwością kolorowania z listy.  
  
    Przykładowy sposób implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsy, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Zobacz także  
 [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowanie składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Instrukcje: Używanie wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)