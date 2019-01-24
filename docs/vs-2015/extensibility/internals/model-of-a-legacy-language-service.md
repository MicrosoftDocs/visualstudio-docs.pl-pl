---
title: Model dla starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d51df6dd11509b86e6648d59978b87d9cd8a02
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795590"
---
# <a name="model-of-a-legacy-language-service"></a>Model starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługa języka definiuje elementy i funkcje dla określonego języka i służy do zapewnienia edytora z użyciem informacji specyficznych dla danego języka. Na przykład edytor musi znać elementów i słów kluczowych języka w celu obsługi kolorowanie składni.  
  
 Usługa językowa ściśle współpracuje z buforu tekstowego zarządzane przez Edytor i widok, który zawiera edytor. Microsoft IntelliSense **Quick Info** opcja znajduje się przykład funkcji udostępniony przez usługę języka.  
  
## <a name="a-minimal-language-service"></a>Usługa języka minimalny  
 Najbardziej podstawowa usługa językowa zawiera dwa następujące obiekty:  
  
- *Usługa językowa* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu. Usługa języka zawierają informacje dotyczące języka, łącznie z nazwy, rozszerzenia nazw plików, Menedżer okien kodu i colorizer.  
  
- *Colorizer* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu.  
  
  Poniższy rysunek koncepcyjny przedstawiający zawiera model usługi w języka podstawowego.  
  
  ![Language Service Model graphic](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Podstawowy język modelu usług  
  
  Hosty okna dokumentu *widok dokumentu* edytora, w tym przypadku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] edytorze podstawowych funkcji. Widok dokumentu i buforu tekstowego są własnością edytora. Te obiekty pracować [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] za pomocą okna dokumentu wyspecjalizowane o nazwie *okna kodu*. W oknie kod znajduje się w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekt, który jest tworzony i kontrolowane przez środowisko IDE.  
  
  Po załadowaniu pliku z danym rozszerzeniem edytora lokalizuje usługa językowa skojarzony z tym rozszerzeniem i przekazuje do niego okna kodu, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Usługa zwraca język *Menedżera okien kodu*, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu.  
  
  Poniższa tabela zawiera omówienie obiekty w modelu.  
  
|Składnik|Obiekt|Funkcja|  
|---------------|------------|--------------|  
|Bufor tekstowy|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode odczytu/zapisu strumienia tekstu. Istnieje możliwość tekstu użyć innego kodowania.|  
|W oknie kodu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Okno dokumentu, który zawiera jeden lub więcej widoków tekstu. Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest w trybie interfejsu wielu dokumentów (MDI), okno kodu jest podrzędnym MDI.|  
|Widok tekstu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Okno, które umożliwia użytkownikowi przejść i wyświetlić tekst przy użyciu klawiatury i myszy. Jako edytora do użytkownika zostanie wyświetlony widok tekstu. Można użyć widoków tekstu w edytorze zwykły system windows, w oknie danych wyjściowych i oknie bezpośrednim. Ponadto można skonfigurować jeden lub więcej widoków tekstu w oknie kodu.|  
|Menedżer tekstu|Zarządza <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługi, z którego można uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> wskaźnika|Składnik, który przechowuje wspólne informacje współużytkowane przez wszystkie składniki, które są opisane wcześniej.|  
|Usługa językowa|Implementacja zależnych; implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Obiekt, który dostarcza informacje specyficzne dla języka, takich jak wyróżnianie składni, uzupełniania instrukcji i parowanie nawiasów klamrowych edytora.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)
