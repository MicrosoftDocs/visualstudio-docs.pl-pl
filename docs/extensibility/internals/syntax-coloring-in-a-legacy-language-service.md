---
title: Kolorowanie składni w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c00e70ed28a8086a87851b978eb7ee6d6077c009
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722974"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej

Program Visual Studio używa usługi kolorowania do identyfikowania elementów języka i wyświetlania ich z określonymi kolorami w edytorze.

## <a name="colorizer-model"></a>Kolorowanie modelu
 Usługa językowa implementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, który jest następnie używany przez edytory. Ta implementacja jest oddzielnym obiektem z usługi językowej, jak pokazano na poniższej ilustracji:

 ![Grafika dotycząca kolorowania SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Usługa kolorowania składni jest oddzielona od ogólnego mechanizmu programu Visual Studio do kolorowania tekstu. Aby uzyskać więcej informacji o ogólnym mechanizmie [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] obkolorowania, zobacz [using Fonts and Colors](../../extensibility/using-fonts-and-colors.md).

 Oprócz kolorowania usługa języka może dostarczać niestandardowe elementy, które są używane przez Edytor, dzięki reklamom, które udostępniają niestandardowe elementy z możliwością obsługi. Można to zrobić przez zaimplementowanie interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> w tym samym obiekcie, który implementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Zwraca liczbę niestandardowych elementów do oddzielenia, gdy Edytor wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> i zwraca indywidualny element, który można kolorować, gdy Edytor wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> zwraca obiekt implementujący interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Jeśli usługa języka obsługuje wartości 24-bitowe lub wysokie kolory, należy zaimplementować interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> na tym samym obiekcie co interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak pakietu VSPackage używa kolorowania usługi językowej

1. Pakietu VSPackage musi uzyskać odpowiednią usługę językową, która wymaga, aby usługa języka pakietu VSPackage:

    1. Użyj obiektu implementującego interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, aby uzyskać kolor tekstu.

         Tekst jest zwykle wyświetlany przy użyciu obiektu, który implementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Pobierz usługę językową, badając dostawcę usług pakietu VSPackage dla identyfikatora GUID usługi językowej. Usługi językowe są identyfikowane w rejestrze przy użyciu rozszerzenia pliku.

    3. Skojarz usługę języka z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. Pakietu VSPackage może teraz uzyskać i używać obiektu Koloruj w następujący sposób:

    > [!NOTE]
    > Pakietów VSPackage, które używają podstawowego edytora, nie muszą jawnie uzyskiwać obiektów kolorystyki usługi językowej. Gdy tylko wystąpienie edytora podstawowego uzyska odpowiednią usługę językową, wszystkie zadania kolorowania są wyświetlane w tym miejscu.

    1. Uzyskaj obiekt kolorystyki usługi językowej, który implementuje interfejsy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dla obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> usługi językowej.

    2. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, aby uzyskać informacje o kolorach dla określonego zakresu tekstu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwraca tablicę wartości, jeden dla każdego znaku w zakresie tekstu. Wartości są indeksami do listy elementów, które są domyślną listą elementów, które są obsługiwane przez Edytor podstawowy lub listę elementów niestandardowych, które są obsługiwane przez samą usługę językową.

    3. Użyj informacji o kolorach zwracanych przez metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, aby wyświetlić zaznaczony tekst.

> [!NOTE]
> Oprócz używania kolorowania usługi językowej pakietu VSPackage może również używać mechanizmu kolorowania tekstu programu Visual Studio ogólnego przeznaczenia. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [using Fonts and Colors](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>W tej sekcji
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)

 W tym artykule omówiono sposób, w jaki Edytor uzyskuje dostęp do funkcji kolorowania składni usługi językowej i co musi implementować usługa języka w celu obsługi kolorowania składni.

- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Pokazuje, jak używać wbudowanych elementów z możliwością kolorów z usługi językowej.

- [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)

 W tym artykule omówiono sposób implementowania niestandardowych elementów z możliwością tworzenia kolorów.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z czcionek i kolorów](../../extensibility/using-fonts-and-colors.md)