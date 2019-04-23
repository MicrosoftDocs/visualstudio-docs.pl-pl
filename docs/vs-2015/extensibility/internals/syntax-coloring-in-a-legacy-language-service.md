---
title: Kolorowanie składni w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2ee09c334394e363d9621ddec887bd5d83726fba
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103579"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używa usługi, kolorowanie, aby zidentyfikować elementy języka i wyświetlać je za pomocą określonego kolorów w edytorze.  
  
## <a name="colorizer-model"></a>Colorizer Model  
 Implementuje usługi w języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs, który jest następnie używany przez edytory. Ta implementacja jest oddzielnym obiektem z usługi języka, jak pokazano na poniższej ilustracji.  
  
 ![Grafika SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Colorizer prostego modelu  
  
> [!NOTE]
>  Kolorowania usługi jest niezależne od ogólnego [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mechanizm Kolorowanie tekstu. Aby uzyskać więcej informacji na temat ogólnych [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] mechanizm obsługi, kolorowanie, zobacz [przy użyciu czcionki i kolory](../../extensibility/using-fonts-and-colors.md).  
  
 Oprócz colorizer usługa językowa może dostarczyć niestandardowe elementy z możliwością kolorowania, które są używane przez Edytor przez reklamy, dostarcza mu niestandardowe elementy z możliwością kolorowania. Można to zrobić poprzez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu na ten sam obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu. Zwraca liczbę niestandardowych elementów z możliwością kolorowania, gdy wywołuje edytora <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody, a zwraca pojedynczy element z możliwością kolorowania niestandardowych, gdy wywołuje edytora <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Metoda zwraca obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu. Jeśli usługa językowa obsługuje kolor 24-bitowego lub o wysokiej wartości, musi on implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu na ten sam obiekt jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak korzysta z pakietu VSPackage Colorizer usługi języka  
  
1. Pakietu VSPackage, należy uzyskać usługi odpowiedni język, która wymaga usługi językowej pakietu VSPackage, wykonaj następujące czynności:  
  
    1. Użyj obiektu Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu, aby uzyskać tekst, który ma być wyróżnione kolorem.  
  
         Tekst jest zwykle wyświetlany za pomocą obiektu, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.  
  
    2. Uzyskaj usługa językowa, badając dostawcy usług z pakietu VSPackage dla usługi w języka identyfikator GUID. Usługi języka są identyfikowane w rejestrze przez rozszerzenie pliku.  
  
    3. Skojarzenia usługi języka o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> przez wywołanie jego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.  
  
2. Pakietu VSPackage teraz uzyskania i używania obiektu colorizer w następujący sposób:  
  
    > [!NOTE]
    >  Pakietów VSPackage, które używają podstawowy edytor nie trzeba uzyskać języka, obiekty colorizer usługi jawnie. Jak najszybciej wystąpienie podstawowy edytor uzyskuje usługi odpowiedni język, wykonuje zadania kolorowanie pokazano poniżej.  
  
    1. Uzyskaj obiekt colorizer usługa języka, który implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfejsów, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody na usłudze językowej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.  
  
    2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby uzyskać informacje colorizer dla określonego zakresu tekstu.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Zwraca tablicę wartości, jeden dla każdego znaku w zakresie tekstu są wyróżnione kolorem. Wartości są indeksy na listę elementów z możliwością kolorowania domyślnej listy elementów z możliwością kolorowania utrzymywane przez podstawowy edytor lub listę niestandardowego elementu z możliwością kolorowania utrzymywane przez samą usługę języka.  
  
    3. Użyj dane kolorowania zwrócony przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę w celu wyświetlenia zaznaczonego tekstu.  
  
> [!NOTE]
>  Oprócz używania colorizer usługi języka, pakietu VSPackage można również użyć ogólnego przeznaczenia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kolorowania mechanizm tekstu. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [przy użyciu czcionki i kolory](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)  
 W tym artykule omówiono, jak edytor uzyskuje dostęp do, kolorowanie składni i jakie usługa językowa musi Implementowanie obsługi składni kolorowania usługi języka.  
  
 [Instrukcje: Używanie wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Pokazuje, jak korzystać z wbudowanych elementów z możliwością kolorowania usługi języka.  
  
 [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)  
 W tym artykule omówiono sposób implementacji niestandardowych elementów z możliwością kolorowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z czcionek i kolorów](../../extensibility/using-fonts-and-colors.md)
