---
title: Kolorowanie składni w edytorach niestandardowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ff717c8586e22d82a79344dd3c134c604f868d10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316652"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowanie składni w edytorach niestandardowych
Edytory wizualne zestawu SDK środowiska Studio, w tym podstawowy edytor używanie usług językowych, aby zidentyfikować konkretne elementy syntaktycznych i wyświetlać je za pomocą kolorów określonego w celu wyświetlenia danego dokumentu.

## <a name="colorization-requirements"></a>Wymagania dotyczące kolorowania
 Wszystkie edytory Implementowanie colorizer usługi języka musi:

1. Użyj obiektu Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Zarządzanie tekst, który ma być pokolorowane i implementacji obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zapewnienie dokumentu widoku tekstu.

2. Uzyskaj interfejsu usługi danego języka, badając dostawcy usług pakietu VSPackage przy użyciu identyfikatora GUID identyfikujący usługi języków.

3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Ta metoda kojarzy usługi języka o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementację, która pakietu VSPackage używa do zarządzania tekst, który ma być wyróżnione kolorem.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Podstawowy edytor użytkowania Colorizer usługi językowej
 Gdy język usługi za pomocą colorizer uzyskuje się przez wystąpienie podstawowy edytor, analizowania i renderowanie tekstu przez colorizer usługi języka odbywa się automatycznie bez jakiejkolwiek dalszej interwencji ze strony użytkownika.

 IDE sposób niewidoczny dla użytkownika:

- Wywołuje colorizer zgodnie z potrzebami, aby przeanalizować i analizowanie tekstu, podczas dodawania lub zmodyfikowany w implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Zapewnia, że wyświetlana dostarczonych przez widok dokumentu, dostarczone przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> wdrożenia są aktualizowane i odświeżana przy użyciu informacji o wypychaniu colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>-Core Editor użytkowania Colorizer usługi językowej
 Edytor dodatkowe wystąpienia można również użyć usługi kolorowanie składni usługi języka, ale jawnie należy pobrać i zastosować colorizer usługi i repaint ich widoków dokumentów, samodzielnie.

 Aby to zrobić, należy edytora-core:

1. Uzyskanie obiektu colorizer usługi języka (który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Robi to przez wywołanie metody pakietu VSPackage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metoda w interfejsie usługi języka.

2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby zażądać kolorowane określonego zakres tekstu.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Metoda zwraca tablicę wartości, jeden dla każdej litery w tekście span są wyróżnione kolorem. Identyfikuje zakres tekstu jako określony typ elementu z możliwością kolorowania, takie jak komentarz, słowo kluczowe lub typu danych.

3. Użyj dane kolorowania zwrócony przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> repaint i wyświetlić jego tekstu.

> [!NOTE]
> Oprócz używania usługi języka colorizer, pakietu VSPackage można użyć ogólnego przeznaczenia mechanizmu Kolorowanie tekstu Visual Studio SDK środowiska. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [przy użyciu czcionki i kolory](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Zobacz też

- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)