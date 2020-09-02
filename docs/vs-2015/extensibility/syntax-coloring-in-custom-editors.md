---
title: Kolorowanie składni w edytorach niestandardowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816910"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowanie składni w edytorach niestandardowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Wystąpienia edytora nierdzeniowego mogą również korzystać z usługi języka kolorowania składni usługi językowej, ale muszą jawnie pobrać i zastosować kolor oraz odświeżenie własnych widoków dokumentów.  
  
 W tym celu wymaga edytora nierdzeniowego, aby:  
  
1. Uzyskaj obiekt kolorystyki usługi językowej (który implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Pakietu VSPackage to przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody w interfejsie usługi językowej.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby zażądać, aby określony zakres tekstu był kolorem.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Metoda zwraca tablicę wartości, po jednej dla każdej litery w przedziale tekstu. Identyfikuje także zakres tekstu jako konkretny typ elementu, na przykład komentarz, słowo kluczowe lub typ danych.  
  
3. Użyj informacji o kolorach zwróconych przez program, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Aby odświeżyć i wyświetlić jego tekst.  
  
> [!NOTE]
> Oprócz używania Kolorka usługi językowej pakietu VSPackage może zdecydować się na użycie mechanizmu kolorowania tekstu zestawu SDK środowiska programu Visual Studio ogólnego przeznaczenia. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [using Fonts and Colors](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)   
 [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)
