---
title: Interfejsy starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się więcej o interfejsach dostępnych w zestawie SDK Visual Studio, które zapewniają starsze funkcje usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75697e1d212b24b743fed62284b384985749fe7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898607"
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy starszej wersji usługi językowej
W przypadku dowolnego konkretnego języka programowania jednocześnie może być tylko jedno wystąpienie usługi językowej. Jednak jedna usługa językowa może obsługiwać więcej niż jeden edytor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie kojarzy usługi językowej z żadnym konkretnym edytorem. W związku z tym podczas żądania operacji usługi językowej należy zidentyfikować odpowiedni edytor jako parametr.

## <a name="common-interfaces-associated-with-language-services"></a>Typowe interfejsy skojarzone z usługami językowym
 Edytor pobiera usługę językową, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> odpowiedni pakiet VSPackage. Identyfikator usługi (SID) przekazany w tym wywołaniu identyfikuje żądaną usługę językową.

 Podstawowe interfejsy usługi językowej można zaimplementować w dowolnej liczbie oddzielnych klas. Jednak typowe podejście to zaimplementowanie następujących interfejsów w jednej klasie:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcjonalnie)

  Interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> musi być zaimplementowany we wszystkich usługach językowych. Zawiera informacje o usłudze językowej, takie jak zlokalizowane nazwy języka, rozszerzenia nazw plików skojarzone z usługą językową i sposób pobierania koloratora.

## <a name="additional-language-service-interfaces"></a>Dodatkowe interfejsy usługi językowej
 Inne interfejsy można dostarczać z usługą językową. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żąda oddzielnego wystąpienia tych interfejsów dla każdego wystąpienia buforu tekstowego. W związku z tym należy zaimplementować każdy z tych interfejsów we własnym obiekcie. W poniższej tabeli przedstawiono interfejsy, które wymagają jednego wystąpienia na wystąpienie buforu tekstowego.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza definiowaniem układów okien kodu, takimi jak pasek listy rozwijanej. Ten interfejs można uzyskać przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody . Istnieje jedno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> okno kodu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Koloruje słowa kluczowe języka i ograniczniki. Ten interfejs można uzyskać przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> jest wywoływana w czasie malowania. Unikaj pracy intensywnie obciążającej obliczenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wewnątrz systemu lub może to mieć niesienie wydajności.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Udostępnia etykietki narzędzi parametrów funkcji IntelliSense. Gdy usługa językowa rozpoznaje znak, który wskazuje, że powinny być wyświetlane dane metody, takie jak nawiasy otwarte, wywołuje metodę w celu powiadomienia widoku tekstowego, że usługa językowa jest gotowa do wyświetlenia etykietki narzędzia informacji o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> parametrach. Następnie widok tekstu wywołuje usługę językową, używając metod interfejsu w celu uzyskania informacji wymaganych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> do wyświetlenia etykietki narzędzia.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Zapewnia uzupełnianie instrukcji IntelliSense. Gdy usługa językowa jest gotowa do wyświetlenia listy uzupełniania, wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę w widoku tekstowym. Następnie widok tekstu wywołuje ponownie usługę językową przy użyciu metod w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> obiekcie .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umożliwia modyfikację widoku tekstu przy użyciu programu obsługi poleceń. Klasa, w której implementuje się <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfejs, musi również implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs. Widok tekstowy pobiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiekt, odpytując <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt przekazywany do metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . Każdy widok powinien <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> mieć jeden obiekt.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje polecenia, które użytkownik typuje w oknie kodu. Monitorowanie danych wyjściowych z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji w celu zapewnienia niestandardowych informacji o ukończeniu i wyświetlania modyfikacji<br /><br /> Aby przekazać <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt do widoku tekstowego, wywołaj . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista kontrolna: Tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
