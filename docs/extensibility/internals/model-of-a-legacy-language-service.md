---
title: Model starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726385"
---
# <a name="model-of-a-legacy-language-service"></a>Model starszej wersji usługi językowej
Usługa języka definiuje elementy i funkcje dla określonego języka i służy do udostępniania edytora informacji specyficznych dla danego języka. Na przykład edytor musi znać elementy i słowa kluczowe języka w celu obsługi kolorowania składni.

 Usługa języka ściśle współpracuje z buforem tekstu zarządzanym przez Edytor i widokiem zawierającym Edytor. Opcja **szybkich informacji** IntelliSense firmy Microsoft jest przykładem funkcji udostępnianej przez usługę języka.

## <a name="a-minimal-language-service"></a>Minimalna usługa języka
 Najbardziej podstawowa usługa języka zawiera dwa następujące obiekty:

- *Usługa językowa* implementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Usługa językowa zawiera informacje o języku, w tym jego nazwę, rozszerzenia nazw plików, Menedżer okien kodu i kolorowanie.

- *Kolor* zaimplementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

  Poniższy rysunek koncepcyjny przedstawia model podstawowej usługi językowej.

  ![Grafika modelu usługi językowej](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Model usługi języka Basic

  Okno dokumentu zawiera *widok dokumentu* edytora, w tym przypadku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podstawowy edytor. Widok dokumentu i bufor tekstowy są własnością edytora. Te obiekty współpracują z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą okna wyspecjalizowanego dokumentu o nazwie *okno kodu*. Okno kod jest zawarte w obiekcie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>, który jest tworzony i kontrolowany przez IDE.

  Po załadowaniu pliku z danym rozszerzeniem Edytor lokalizuje usługę języka skojarzoną z tym rozszerzeniem i przekazuje do niej okno kodu, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Usługa języka zwraca *Menedżera okien kodu*, który implementuje interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.

  Poniższa tabela zawiera omówienie obiektów w modelu.

| Składnik | Obiekt | Funkcja |
|------------------| - | - |
| Bufor tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Strumień tekstowy do odczytu/zapisu w formacie Unicode. Użycie innych kodowań jest możliwe w przypadku tekstu. |
| Okno kodu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu, które zawiera co najmniej jeden widok tekstu. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest w trybie interfejsu wielu dokumentów (MDI), okno kod jest elementem podrzędnym MDI. |
| Widok tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, które umożliwia użytkownikowi nawigowanie i wyświetlanie tekstu przy użyciu klawiatury i myszy. Widok tekstu jest widoczny dla użytkownika jako edytor. Możesz użyć widoków tekstowych w zwykłych oknach edytora, oknie danych wyjściowych i oknie bezpośrednim. Ponadto można skonfigurować jeden lub więcej widoków tekstu w oknie kodu. |
| Menedżer tekstu | Zarządzane przez usługę <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>, z której uzyskuje się wskaźnik <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Składnik, który przechowuje wspólne informacje udostępniane przez wszystkie opisane wcześniej składniki. |
| Usługa języka | Zależne od implementacji; implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Obiekt, który zapewnia Edytor z informacjami specyficznymi dla języka, takimi jak wyróżnianie składni, uzupełnianie instrukcji i nawiasy klamrowe. |

## <a name="see-also"></a>Zobacz także
- [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)