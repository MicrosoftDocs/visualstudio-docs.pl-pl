---
title: Interfejsy usługi starszego języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5e574267ac83d145c5f3fb44117534127e3f1fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785849"
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dla określonego języka programowania jednocześnie może istnieć tylko jedno wystąpienie usługi języka. Jednak usługa jeden język może obsługiwać więcej niż jeden z nich.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kojarzy usługi językowej z dowolnego określonego edytora. W związku z tym w przypadku żądania operacji usługi języka, należy zidentyfikować odpowiedniego edytora jako parametr.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Wspólnych interfejsów skojarzone z usługami języka  
 Edytor pobiera usługi języka, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na odpowiednie pakietu VSPackage. Identyfikator przekazanego to wywołanie usługi identyfikuje żądanej usługi języka.  
  
 Interfejsy usługi w języka core można zaimplementować na dowolnej liczbie osobnych klas. Jednak typowym podejściem jest wdrożenie następujących interfejsów w jednej klasy:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcjonalnie)  
  
  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Interfejsu muszą być zaimplementowane na wszystkie usługi w języka. Zawiera informacje dotyczące usługi języka, takie jak nazwa zlokalizowanego języka rozszerzeń nazw plików, które są skojarzone z usługi języka oraz jak pobierać colorizer.  
  
## <a name="additional-language-service-interfaces"></a>Interfejsy usługi dodatkowych języków  
 Inne interfejsy mogą otrzymywać przy użyciu usługi języka. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] żąda osobne wystąpienie te interfejsy, dla każdego wystąpienia bufor tekstowy. W związku z tym należy zaimplementować każdy z tych interfejsów własnego obiektu. W poniższej tabeli przedstawiono interfejsy, które wymagają jedno wystąpienie każdego wystąpienia buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza zakończeń okna kodu, takich jak pasek listy rozwijanej. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Istnieje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> na oknie kodu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Kolorowania ograniczników i słowa kluczowe języka. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> jest wywoływana w czasie malowania. Należy unikać pracy najintensywniejszej obliczeniowo wewnątrz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> lub może to spowodować obniżenie wydajności.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zapewnia etykietki narzędzi IntelliSense parametru. Gdy usługa języka rozpoznaje znak, który wskazuje danych tej metody powinna być wyświetlana, takich jak nawias otwierający wywoływanych przez nią <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę, aby powiadomić tekst view, które usługa języka jest gotowa do wyświetlana etykietka narzędzia informacje o parametrze. Widok tekstu następnie ponownie wywołuje usługa językowa przez przy użyciu metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu można pobrać informacji wymaganych do wyświetlenia wskazówki.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Udostępnia instrukcji IntelliSense. Gdy usługa języka jest gotowy do wyświetlenia listy uzupełniania, wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w widoku tekstu. Widok tekstu następnie ponownie wywołuje usługa językowa przez przy użyciu metod na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> obiektu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umożliwia modyfikowanie widoku tekstu za pomocą obsługi poleceń. Klasy należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interfejs musi implementować też <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Pobiera widok tekstu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiektu, badając <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektu, który jest przekazywany do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Powinien istnieć tylko jeden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiekt dla każdego widoku.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje polecenia użytkownik wpisze do okna kodu. Monitoruj dane wyjściowe z Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, aby podać informacje o niestandardowych ukończenia i wyświetlić modyfikacji<br /><br /> Do przekazania swojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt widoku tekstu wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista kontrolna: tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

