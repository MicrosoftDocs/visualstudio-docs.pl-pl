---
title: Kolorowanki składni w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704759"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej

Visual Studio używa usługi kolorowania do identyfikowania elementów języka i wyświetlania ich z określonymi kolorami w edytorze.

## <a name="colorizer-model"></a>Model barwiącego
 Usługa języka implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs, który jest następnie używany przez edytorów. Ta implementacja jest oddzielnym obiektem od usługi języka, jak pokazano na poniższej ilustracji:

 ![Grafika graficzna SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Usługa kolorowania składni jest oddzielona od ogólnego mechanizmu programu Visual Studio do kolorowania tekstu. Aby uzyskać więcej [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] informacji na temat ogólnego mechanizmu obsługującego kolorowanie, zobacz [Używanie czcionek i kolorów](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Oprócz colorizer, usługa języka może dostarczyć niestandardowe elementy colorable, które są używane przez edytora, reklamując, że dostarcza niestandardowe elementy colorable. Można to zrobić, implementując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejs na tym samym <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiekcie, który implementuje interfejs. Zwraca liczbę niestandardowych elementów colorable, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> gdy edytor wywołuje metodę i zwraca pojedynczy element <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> niestandardowy kolorowalny, gdy edytor wywołuje metodę.

 Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> zwraca obiekt, który <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> implementuje interfejs. Jeśli usługa języka obsługuje 24-bitowe lub wysokie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> wartości kolorów, musi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> implementować interfejs na tym samym obiekcie co interfejs.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak VSPackage używa colorizer usługi języka

1. VsPackage musi uzyskać odpowiednią usługę języka, która wymaga usługi języka VSPackage, aby wykonać następujące czynności:

    1. Użyj obiektu implementującego interfejs, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> aby uzyskać tekst do pokolorowania.

         Tekst jest zazwyczaj wyświetlany przy użyciu obiektu, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejs.

    2. Pobierz usługę języka, odwołując się do dostawcy usług vspackage dla identyfikatora GUID usługi języka. Usługi językowe są identyfikowane w rejestrze przez rozszerzenie pliku.

    3. Skojarz usługę języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> z wywołaniem jej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.

2. VSPackage można teraz uzyskać i używać colorizer obiektu w następujący sposób:

    > [!NOTE]
    > Pakiety VSPackages, które używają edytora podstawowego nie trzeba uzyskać usługi języka colorizer obiektów jawnie. Jak tylko wystąpienie edytora podstawowego uzyskuje odpowiednią usługę języka, wykonuje wszystkie zadania kolorowania pokazane w tym miejscu.

    1. Uzyskaj obiekt colorizer usługi języka, który <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , i interfejsy, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> na obiekcie usługi języka.

    2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody, aby uzyskać informacje colorizer dla określonego zakresu tekstu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>zwraca tablicę wartości, po jednej dla każdego znaku w zakresie tekstu, który jest barwiony. Wartości są indeksami do listy elementów colorable, który jest domyślną listę elementów colorable obsługiwane przez edytora rdzenia lub niestandardowej listy elementów colorable obsługiwane przez samą usługę języka.

    3. Użyj informacji o koloryzacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwróconych przez metodę, aby wyświetlić zaznaczony tekst.

> [!NOTE]
> Oprócz korzystania z colorizer usługi języka VSPackage można również użyć ogólnego przeznaczenia visual studio kolorowanie tekstu mechanizmu. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [Korzystanie z czcionek i kolorów](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>W tej sekcji
- [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)

 W tym artykule omówiono sposób, w jaki edytor uzyskuje dostęp do kolorowania składni usługi języka i co usługa języka musi zaimplementować do obsługi kolorowania składni.

- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Pokazuje, jak używać wbudowanych elementów colorable z usługi języka.

- [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)

 W tym artykule omówiono sposób implementowania niestandardowych elementów colorable.
