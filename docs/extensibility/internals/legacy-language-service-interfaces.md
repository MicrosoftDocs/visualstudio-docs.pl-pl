---
title: Starsze interfejsy usługi językowej | Microsoft Docs
description: Dowiedz się więcej o interfejsach dostępnych w zestawie SDK programu Visual Studio, które udostępniają starsze funkcje usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f6010ffdf6873073eded63c75475115391a3964
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839602"
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy starszej wersji usługi językowej
W przypadku każdego określonego języka programowania w danym momencie może istnieć tylko jedno wystąpienie usługi językowej. Jednak pojedyncza usługa języka może obsłużyć więcej niż jeden edytor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie kojarzy usługi językowej z żadnym konkretnym edytorem. W związku z tym po zażądaniu operacji usługi językowej należy zidentyfikować odpowiedni edytor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Typowe interfejsy skojarzone z usługami językowymi
 Edytor pobiera usługę językową, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> odpowiednie pakietu VSPackage. Identyfikator usługi (SID) zakończony przez to wywołanie identyfikuje żądaną usługę języka.

 Podstawowe interfejsy usługi językowej można zaimplementować na dowolnej liczbie oddzielnych klas. Jednak typowym podejściem jest zaimplementowanie następujących interfejsów w jednej klasie:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcjonalnie)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Interfejs musi być zaimplementowany dla wszystkich usług językowych. Zawiera informacje o usłudze językowej, takie jak zlokalizowana nazwa języka, rozszerzenia nazw plików skojarzone z usługą języka oraz sposób pobierania kolorki.

## <a name="additional-language-service-interfaces"></a>Dodatkowe interfejsy usługi językowej
 Inne interfejsy można dostarczać z usługą języka. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda osobnego wystąpienia tych interfejsów dla każdego wystąpienia buforu tekstu. W związku z tym należy zaimplementować każdy z tych interfejsów na swoim obiekcie. W poniższej tabeli przedstawiono interfejsy, które wymagają jednego wystąpienia na wystąpienie buforu tekstu.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza zakończeniami okna kodu, takimi jak pasek menu rozwijanego. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Istnieje jedno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> dla każdego okna kodu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Koloruje słowa kluczowe i ograniczniki języka. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> jest wywoływana w czasie malowania. Unikaj pracy wymagającej intensywnych obliczeń w porównaniu z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wydajnością.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zawiera etykietki narzędzi funkcji IntelliSense. Gdy usługa języka rozpoznaje znak wskazujący, że dane metody powinny być wyświetlane, takie jak otwarty nawias, wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę w celu powiadomienia widoku tekstu, że usługa języka jest gotowa do wyświetlania etykietki narzędzia informacji o parametrach. Następnie widok tekstu wywołuje z powrotem do usługi językowej przy użyciu metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu, aby uzyskać informacje wymagane do wyświetlenia etykietki narzędzia.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Zawiera uzupełnienie instrukcji IntelliSense. Gdy usługa języka jest gotowa do wyświetlenia listy uzupełniania, wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę w widoku tekstu. Następnie widok tekstu wywołuje z powrotem do usługi językowej przy użyciu metod dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> obiektu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Zezwala na modyfikowanie widoku tekstu przy użyciu programu obsługi poleceń. Klasa, w której zaimplementowano <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfejs, również musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs. Widok tekstu pobiera obiekt, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> badając <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt, który jest przesyłany do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Każdy widok powinien mieć jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiekt.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje polecenia, które użytkownik wpisze do okna kod. Monitoruj dane wyjściowe z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, aby udostępniać niestandardowe informacje o uzupełnianiu i modyfikować widok<br /><br /> Aby przekazać <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt do widoku tekstu, wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista kontrolna: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
