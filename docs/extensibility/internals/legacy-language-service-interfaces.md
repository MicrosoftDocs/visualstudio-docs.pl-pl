---
title: Starsze interfejsy usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726846"
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy starszej wersji usługi językowej
W przypadku każdego określonego języka programowania w danym momencie może istnieć tylko jedno wystąpienie usługi językowej. Jednak pojedyncza usługa języka może obsłużyć więcej niż jeden edytor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie kojarzy usługi językowej z żadnym konkretnym edytorem. W związku z tym po zażądaniu operacji usługi językowej należy zidentyfikować odpowiedni edytor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Typowe interfejsy skojarzone z usługami językowymi
 Edytor pobiera usługę językową, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na odpowiednich pakietu VSPackage. Identyfikator usługi (SID) zakończony przez to wywołanie identyfikuje żądaną usługę języka.

 Podstawowe interfejsy usługi językowej można zaimplementować na dowolnej liczbie oddzielnych klas. Jednak typowym podejściem jest zaimplementowanie następujących interfejsów w jednej klasie:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcjonalnie)

  Interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> musi być zaimplementowany dla wszystkich usług językowych. Zawiera informacje o usłudze językowej, takie jak zlokalizowana nazwa języka, rozszerzenia nazw plików skojarzone z usługą języka oraz sposób pobierania kolorki.

## <a name="additional-language-service-interfaces"></a>Dodatkowe interfejsy usługi językowej
 Inne interfejsy można dostarczać z usługą języka. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda osobnego wystąpienia tych interfejsów dla każdego wystąpienia buforu tekstu. W związku z tym należy zaimplementować każdy z tych interfejsów na swoim obiekcie. W poniższej tabeli przedstawiono interfejsy, które wymagają jednego wystąpienia na wystąpienie buforu tekstu.

|Interface|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza zakończeniami okna kodu, takimi jak pasek menu rozwijanego. Ten interfejs można uzyskać za pomocą metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Istnieje jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> na okno kodu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Koloruje słowa kluczowe i ograniczniki języka. Ten interfejs można uzyskać za pomocą metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> jest wywoływana w czasie malowania. Unikaj pracy wymagającej intensywnych obliczeń w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> lub wydajności.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zawiera etykietki narzędzi funkcji IntelliSense. Gdy usługa języka rozpoznaje znak wskazujący, że dane metody powinny być wyświetlane, takie jak otwarty nawias, wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>, aby powiadomić Widok tekstowy o gotowości usługi językowej do wyświetlenia etykietki narzędzia informacji o parametrach. Widok tekstu następnie wywołuje z powrotem do usługi językowej przy użyciu metod interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>, aby uzyskać informacje wymagane do wyświetlenia etykietki narzędzia.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Zawiera uzupełnienie instrukcji IntelliSense. Gdy usługa języka jest gotowa do wyświetlenia listy uzupełniania, wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> w widoku tekstu. Następnie widok tekstu wywołuje z powrotem do usługi językowej przy użyciu metod w obiekcie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Zezwala na modyfikowanie widoku tekstu przy użyciu programu obsługi poleceń. Klasa, w której zaimplementowano interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>, również musi implementować interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Widok tekstu pobiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiektu, wykonując zapytania o obiekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, który jest przesyłany do metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>. Dla każdego widoku powinien istnieć jeden obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje polecenia, które użytkownik wpisze do okna kod. Monitoruj dane wyjściowe z implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, aby zapewnić niestandardowe informacje o uzupełnianiu i modyfikować widok<br /><br /> Aby przekazać obiekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> do widoku tekstu, wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|

## <a name="see-also"></a>Zobacz także
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista kontrolna: tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)