---
title: Kolorowanie składni w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59d25c338cb0c7406c533afeceaf3675fbd16e96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815199"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używa usługi kolorowania do identyfikowania elementów języka i wyświetlania ich przy użyciu określonych kolorów w edytorze.  
  
## <a name="colorizer-model"></a>Kolorowanie modelu  
 Usługa językowa implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs, który jest następnie używany przez edytory. Ta implementacja jest oddzielnym obiektem z usługi językowej, jak pokazano na poniższej ilustracji.  
  
 ![Grafika dotycząca kolorowania SVC](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Prosty model kolorowania  
  
> [!NOTE]
> Usługa kolorowania składni jest oddzielona od ogólnego [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mechanizmu kolorowania tekstu. Aby uzyskać więcej informacji o ogólnym [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mechanizmie, który obsługuje kolorowanie, zobacz [using Fonts and Colors](../../extensibility/using-fonts-and-colors.md).  
  
 Oprócz kolorowania usługa języka może dostarczać niestandardowe elementy, które są używane przez Edytor przez reklamę, że udostępniają niestandardowe elementy z możliwością obsługi. Można to zrobić przez zaimplementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu w tym samym obiekcie, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs. Zwraca liczbę niestandardowych elementów do oddzielenia, gdy Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodę i zwraca indywidualny, niestandardowy element, który jest wywoływany przez Edytor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Metoda zwraca obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejs. Jeśli usługa językowa obsługuje wartości 24-bitowe lub o wysokim kolorze, musi zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejs na tym samym obiekcie co <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejs.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak pakietu VSPackage używa kolorowania usługi językowej  
  
1. Pakietu VSPackage musi uzyskać odpowiednią usługę językową, która wymaga, aby usługa języka pakietu VSPackage:  
  
    1. Użyj obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejs, aby wyświetlić kolor tekstu.  
  
         Tekst jest zwykle wyświetlany przy użyciu obiektu, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejs.  
  
    2. Pobierz usługę językową, badając dostawcę usług pakietu VSPackage dla identyfikatora GUID usługi językowej. Usługi językowe są identyfikowane w rejestrze przy użyciu rozszerzenia pliku.  
  
    3. Skojarz usługę języka z metodą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> wywołującą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodę.  
  
2. Pakietu VSPackage może teraz uzyskać i używać obiektu Koloruj w następujący sposób:  
  
    > [!NOTE]
    > Pakietów VSPackage, które używają podstawowego edytora, nie musi jawnie uzyskiwać obiektów kolorystyki usługi językowej. Gdy tylko wystąpienie edytora podstawowego uzyska odpowiednią usługę językową, wszystkie zadania kolorowania są wyświetlane w tym miejscu.  
  
    1. Uzyskaj obiekt Koloruj usługi językowej, który implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` interfejsy, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodę dla obiektu usługi językowej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  
  
    2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby uzyskać informacje o kolorach dla określonego zakresu tekstu.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwraca tablicę wartości, jeden dla każdego znaku w zakresie tekstu. Wartości są indeksami do listy elementów, które są domyślną listą elementów, które są obsługiwane przez Edytor podstawowy lub listę elementów niestandardowych, które są obsługiwane przez samą usługę językową.  
  
    3. Użyj informacji o kolorach zwracanych przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę w celu wyświetlenia zaznaczonego tekstu.  
  
> [!NOTE]
> Oprócz używania kolorowania usługi językowej pakietu VSPackage może również używać [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mechanizmu kolorowania tekstu ogólnego przeznaczenia. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [using Fonts and Colors](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)  
 W tym artykule omówiono sposób, w jaki Edytor uzyskuje dostęp do funkcji kolorowania składni usługi językowej i co musi implementować usługa języka w celu obsługi kolorowania składni.  
  
 [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Pokazuje, jak używać wbudowanych elementów z możliwością kolorów z usługi językowej.  
  
 [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)  
 W tym artykule omówiono sposób implementowania niestandardowych elementów z możliwością tworzenia kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z czcionek i kolorów](../../extensibility/using-fonts-and-colors.md)
