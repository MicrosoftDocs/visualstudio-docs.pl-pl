---
title: Interfejsy usługi języka starszego języka | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707384"
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy starszej wersji usługi językowej
Dla każdego określonego języka programowania może istnieć tylko jedno wystąpienie usługi języka w danym momencie. Jednak usługa jednego języka może obsługiwać więcej niż jeden edytor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nie kojarzy usługi językowej z żadnym konkretnym edytorem. W związku z tym podczas żądania operacji usługi języka, należy zidentyfikować odpowiedni edytor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Typowe interfejsy skojarzone z usługami językowymi
 Edytor pobiera usługi języka, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> wywołując odpowiednie VSPackage. Identyfikator usługi (SID) przekazany w tym wywołaniu identyfikuje żądaną usługę języka.

 Interfejsy usługi języka podstawowego można zaimplementować w dowolnej liczbie oddzielnych klas. Jednak wspólne podejście jest zaimplementowanie następujących interfejsów w jednej klasie:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcjonalnie)

  Interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> musi być zaimplementowany we wszystkich usługach językowych. Zawiera informacje o usłudze języka, takie jak zlokalizowana nazwa języka, rozszerzenia nazw plików skojarzone z usługą języka i sposób pobierania colorizer.

## <a name="additional-language-service-interfaces"></a>Dodatkowe interfejsy usług językowych
 Inne interfejsy mogą być dostarczane z usługą językową. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]żąda osobnego wystąpienia tych interfejsów dla każdego wystąpienia buforu tekstu. W związku z tym należy zaimplementować każdy z tych interfejsów na własny obiekt. W poniższej tabeli przedstawiono interfejsy, które wymagają jednego wystąpienia na wystąpienie buforu tekstu.

|Interface|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza ozdobami okna kodu, takimi jak pasek rozwijany. Ten interfejs można uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> przy użyciu metody. Istnieje jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> na okno kodu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Koloruje słowa kluczowe języka i ograniczniki. Ten interfejs można uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> przy użyciu metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>nazywa się w czasie malowania. Unikaj pracy intensywnie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> korzystającej z obliczeń wewnątrz lub wydajność może ucierpieć.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zawiera etykietki narzędzi parametrów IntelliSense. Gdy usługa języka rozpoznaje znak, który wskazuje, że powinny być wyświetlane dane metody, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> takie jak otwarty nawias, wywołuje metodę powiadamiania widoku tekstowego, że usługa języka jest gotowa do wyświetlenia etykietki narzędzia informacje o parametrach. Widok tekstu następnie wywołuje z powrotem do usługi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> języka przy użyciu metod interfejsu, aby uzyskać wymagane informacje do wyświetlania etykietki narzędzia.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Zapewnia zakończenie instrukcji IntelliSense. Gdy usługa językowa jest gotowa do wyświetlenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> listy uzupełnień, wywołuje metodę w widoku tekstowym. Widok tekstu następnie wywołuje z powrotem do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> usługi języka przy użyciu metod na obiekcie.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umożliwia modyfikację widoku tekstu za pomocą programu obsługi poleceń. Klasa, w której <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> zaimplementujesz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, musi również implementować interfejs. Widok tekstu pobiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiekt, odpytując <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> który jest przekazywany do metody. Dla każdego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> widoku powinien istnieć jeden obiekt.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje polecenia, które użytkownik wpisuje w oknie kodu. Monitorowanie danych <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> wyjściowych z implementacji w celu zapewnienia niestandardowych informacji o zakończeniu i wyświetlania modyfikacji<br /><br /> Aby przekazać <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt do widoku <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>tekstowego, zadzwoń do .|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista kontrolna: tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
