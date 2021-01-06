---
title: Model starszej wersji usługi językowej | Microsoft Docs
description: Ten model minimalnej usługi językowej dla edytora podstawowego programu Visual Studio jest używany jako przewodnik tworzenia własnej usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2928d3c09a54ea8e9548f7751381279f153643e5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876743"
---
# <a name="model-of-a-legacy-language-service"></a>Model starszej wersji usługi językowej
Usługa języka definiuje elementy i funkcje dla określonego języka i służy do udostępniania edytora informacji specyficznych dla danego języka. Na przykład edytor musi znać elementy i słowa kluczowe języka w celu obsługi kolorowania składni.

 Usługa języka ściśle współpracuje z buforem tekstu zarządzanym przez Edytor i widokiem zawierającym Edytor. Opcja **szybkich informacji** IntelliSense firmy Microsoft jest przykładem funkcji udostępnianej przez usługę języka.

## <a name="a-minimal-language-service"></a>Minimalna usługa języka
 Najbardziej podstawowa usługa języka zawiera dwa następujące obiekty:

- *Usługa językowa* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs. Usługa językowa zawiera informacje o języku, w tym jego nazwę, rozszerzenia nazw plików, Menedżer okien kodu i kolorowanie.

- *Kolor* zaimplementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs.

  Poniższy rysunek koncepcyjny przedstawia model podstawowej usługi językowej.

  ![Grafika modelu usługi językowej](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Model usługi języka Basic

  Okno dokumentu zawiera *widok dokumentu* edytora, w tym przypadku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podstawowy edytor. Widok dokumentu i bufor tekstowy są własnością edytora. Te obiekty współpracują z programem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą wyspecjalizowanego okna dokumentu o nazwie *okno kodu*. Okno kod jest zawarte w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekcie, który jest tworzony i kontrolowany przez IDE.

  Po załadowaniu pliku z danym rozszerzeniem Edytor lokalizuje usługę języka skojarzoną z tym rozszerzeniem i przekazuje do niej okno kodu, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodę. Usługa języka zwraca *Menedżera okien kodu*, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejs.

  Poniższa tabela zawiera omówienie obiektów w modelu.

| Składnik | Obiekt | Funkcja |
|------------------| - | - |
| Bufor tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Strumień tekstowy do odczytu/zapisu w formacie Unicode. Użycie innych kodowań jest możliwe w przypadku tekstu. |
| Okno kodu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu, które zawiera co najmniej jeden widok tekstu. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest w trybie interfejsu wielu dokumentów (MDI), okno kod jest elementem podrzędnym MDI. |
| Widok tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, które umożliwia użytkownikowi nawigowanie i wyświetlanie tekstu przy użyciu klawiatury i myszy. Widok tekstu jest widoczny dla użytkownika jako edytor. Możesz użyć widoków tekstowych w zwykłych oknach edytora, oknie danych wyjściowych i oknie bezpośrednim. Ponadto można skonfigurować jeden lub więcej widoków tekstu w oknie kodu. |
| Menedżer tekstu | Zarządzane przez <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługę, z którego uzyskujesz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> wskaźnik | Składnik, który przechowuje wspólne informacje udostępniane przez wszystkie opisane wcześniej składniki. |
| Usługa języka | Zależne od implementacji; wprowadza <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Obiekt, który zapewnia Edytor z informacjami specyficznymi dla języka, takimi jak wyróżnianie składni, uzupełnianie instrukcji i nawiasy klamrowe. |

## <a name="see-also"></a>Zobacz też
- [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)
