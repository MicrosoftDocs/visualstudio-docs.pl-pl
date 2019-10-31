---
title: Kolorowanie składni w edytorach niestandardowych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a62fd7a8ab0673d6a6020fb7d73f04488ff23485
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188860"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowanie składni w edytorach niestandardowych
Edytory SDK środowiska programu Visual Studio, w tym podstawowy edytor, wykorzystują usługi językowe do identyfikowania określonych elementów składniowych i wyświetlania ich z określonymi kolorami dla danego widoku dokumentu.

## <a name="colorization-requirements"></a>Wymagania dotyczące kolorowania
 Wszystkie edytory implementujące kolor koloru usługi językowej muszą:

1. Użyj obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, aby zarządzać tekstem w celu uzyskania koloru i obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> w celu udostępnienia widoku dokumentu dla tekstu.

2. Uzyskaj interfejs do określonej usługi językowej, badając dostawcę usług pakietu VSPackage przy użyciu identyfikującego go identyfikatora GUID usługi.

3. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Ta metoda kojarzy usługę języka z implementacją <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, której pakietu VSPackage używa do zarządzania tekstem, który ma być kolorem.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Użycie podstawowego edytora dla kolorowania usługi językowej
 Gdy usługa językowa ze kolorem jest uzyskiwana przez wystąpienie podstawowego edytora, analizowanie i renderowanie tekstu przez kolorowanie przez program obsługi języka odbywa się automatycznie, bez konieczności dalszej interwencji z Twojej strony.

 Środowisko IDE w sposób przezroczysty:

- Wywołuje kolor w miarę potrzeby, aby analizować i analizować tekst w miarę ich dodawania lub modyfikowania w implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Zapewnia, że wyświetlanie dostarczone przez widok dokumentu zapewniane przez implementację <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> jest aktualizowane i odświeżane przy użyciu informacji zwracanych przez kolor.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Użycie nierdzeniowego edytora kolorowania usługi języka
 Wystąpienia edytora nierdzeniowego mogą również używać usługi języka do tworzenia kolorowania składni, ale muszą jawnie pobierać i stosować kolorowanie, a także odświeżać własne widoki dokumentów.

 W tym celu niepodstawowy Edytor musi:

1. Uzyskaj obiekt kolorystyki usługi językowej (który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Pakietu VSPackage to przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> w interfejsie usługi językowej.

2. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, aby zażądać przebarwienia określonego zakresu tekstu.

     Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwraca tablicę wartości, jedną dla każdej litery w przedziale tekstu. Identyfikuje także zakres tekstu jako konkretny typ elementu, na przykład komentarz, słowo kluczowe lub typ danych.

3. Użyj informacji o kolorach zwracanych przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, aby odświeżyć i wyświetlić jego tekst.

> [!NOTE]
> Oprócz używania Kolorka usługi językowej pakietu VSPackage może zdecydować się na użycie mechanizmu kolorowania tekstu zestawu SDK środowiska programu Visual Studio ogólnego przeznaczenia. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [using Fonts and Colors](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Zobacz także

- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)