---
title: Kolorowanie składni w edytorach niestandardowych | Microsoft Docs
description: Dowiedz się więcej na temat kolorowania składni w edytorach niestandardowych zestawu SDK środowiska Visual Studio, w którym są wyświetlane określone kolory dla danego widoku dokumentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aac72cbc26ff5e6abf96259fd161cba63b3b2af
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716071"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowanie składni w edytorach niestandardowych
Edytory SDK środowiska programu Visual Studio, w tym podstawowy edytor, wykorzystują usługi językowe do identyfikowania określonych elementów składniowych i wyświetlania ich z określonymi kolorami dla danego widoku dokumentu.

## <a name="colorization-requirements"></a>Wymagania dotyczące kolorowania
 Wszystkie edytory implementujące kolor koloru usługi językowej muszą:

1. Użyj obiektu implementującego, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Aby zarządzać tekstem w celu uzyskania koloru i obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> w celu udostępnienia widoku dokumentu tekstu.

2. Uzyskaj interfejs do określonej usługi językowej, badając dostawcę usług pakietu VSPackage przy użyciu identyfikującego go identyfikatora GUID usługi.

3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodę implementującą obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Ta metoda kojarzy usługę języka z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementacją używaną przez pakietu VSPackage do zarządzania tekstem, który ma być kolorem.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Użycie podstawowego edytora dla kolorowania usługi językowej
 Gdy usługa językowa ze kolorem jest uzyskiwana przez wystąpienie podstawowego edytora, analizowanie i renderowanie tekstu przez kolorowanie przez program obsługi języka odbywa się automatycznie, bez konieczności dalszej interwencji z Twojej strony.

 Środowisko IDE w sposób przezroczysty:

- Wywołuje kolor w miarę potrzeby, aby analizować i analizować tekst w miarę ich dodawania lub modyfikowania w implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Zapewnia, że wyświetlanie dostarczone przez widok dokumentu zapewniane przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementację jest aktualizowane i odświeżane przy użyciu informacji zwracanych przez kolor.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Użycie nierdzeniowego edytora kolorowania usługi języka
 Wystąpienia edytora nierdzeniowego mogą również używać usługi języka do tworzenia kolorowania składni, ale muszą jawnie pobierać i stosować kolorowanie, a także odświeżać własne widoki dokumentów.

 W tym celu niepodstawowy Edytor musi:

1. Uzyskaj obiekt kolorystyki usługi językowej (który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Pakietu VSPackage to przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody w interfejsie usługi językowej.

2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby zażądać, aby określony zakres tekstu był kolorem.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Metoda zwraca tablicę wartości, po jednej dla każdej litery w przedziale tekstu. Identyfikuje także zakres tekstu jako konkretny typ elementu, na przykład komentarz, słowo kluczowe lub typ danych.

3. Użyj informacji o kolorach zwróconych przez program, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Aby odświeżyć i wyświetlić jego tekst.

> [!NOTE]
> Oprócz używania Kolorka usługi językowej pakietu VSPackage może zdecydować się na użycie mechanizmu kolorowania tekstu zestawu SDK środowiska programu Visual Studio ogólnego przeznaczenia. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [using Fonts and Colors](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Zobacz też

- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)