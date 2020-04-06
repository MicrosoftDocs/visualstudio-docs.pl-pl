---
title: Kolorowanki składni w edytorach niestandardowych | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699338"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowanie składni w edytorach niestandardowych
Edytory SDK środowiska programu Visual Studio, w tym edytor podstawowy, używają usług językowych do identyfikowania określonych elementów syntaktycznych i wyświetlania ich z określonymi kolorami dla danego widoku dokumentu.

## <a name="colorization-requirements"></a>Wymagania dotyczące koloryzacji
 Wszyscy redaktorzy implementujący colorizer usługi językowej muszą:

1. Za pomocą obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementującego do zarządzania tekstem, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> który ma być pokolorowany, i obiektem implementującym, aby zapewnić widok dokumentu tekstu.

2. Uzyskaj interfejs do usługi określonego języka, wykonując kwerendę dostawcy usług VSPackage przy użyciu identyfikatora GUID identyfikującej usługę języków.

3. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>obiektu . Ta metoda kojarzy usługę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> języka z implementacją, której program VSPackage używa do zarządzania tekstem, który ma być pokolorowany.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Korzystanie z core editor colorizer usługi językowej
 Gdy usługa języka z koloryskiem jest uzyskiwana przez wystąpienie edytora podstawowego, analizowanie i renderowanie tekstu za pomocą kolorowacza usługi językowej odbywa się automatycznie bez konieczności dalszej interwencji z Twojej strony.

 IDE w sposób przejrzysty:

- Wywołuje koloryzator w razie potrzeby do analizowania i analizowania tekstu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>który jest dodawany lub modyfikowany w implementacji programu .

- Zapewnia, że wyświetlanie dostarczone przez widok <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dokumentu dostarczone przez implementację jest aktualizowany i odświeżany przy użyciu informacji zwracanych przez colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Użycie edytora niepodstawowego w colorizerze usługi językowej
 Wystąpienia edytora innych niż podstawowe można również użyć usługi kolorowania składni usługi języka, ale muszą jawnie pobrać i zastosować colorizer usługi i odświeżyć ich widoki dokumentu siebie.

 Aby to zrobić, edytor nie-core musi:

1. Uzyskaj obiekt colorizer usługi językowej (który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage robi to, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> wywołując metodę w interfejsie usługi języka.

2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby zażądać, aby określony zakres tekstu był pokolorowany.

     Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zwraca tablicę wartości, po jednej dla każdej litery w zakresie tekstu, który jest pokolorowany. Identyfikuje również zakres tekstu jako określony typ elementu colorable, takich jak komentarz, słowo kluczowe lub typ danych.

3. Użyj informacji o koloryzacji zwróconych przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> odświeżyć i wyświetlić jego tekst.

> [!NOTE]
> Oprócz korzystania z colorizer usługi języka VSPackage można wybrać do korzystania z ogólnego przeznaczenia Visual Studio Środowiska SDK kolorowanie tekstu mechanizmu. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [Korzystanie z czcionek i kolorów](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>Zobacz też

- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)
