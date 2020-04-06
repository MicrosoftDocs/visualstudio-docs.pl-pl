---
title: Model usługi języka starszego | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707050"
---
# <a name="model-of-a-legacy-language-service"></a>Model starszej wersji usługi językowej
Usługa języka definiuje elementy i funkcje dla określonego języka i jest używana do dostarczania edytorowi informacji specyficznych dla tego języka. Na przykład edytor musi znać elementy i słowa kluczowe języka w celu obsługi kolorowania składni.

 Usługa języka ściśle współpracuje z buforem tekstu zarządzanym przez edytora i widoku, który zawiera edytor. Opcja Microsoft IntelliSense **Quick Info** jest przykładem funkcji udostępnianej przez usługę językową.

## <a name="a-minimal-language-service"></a>Minimalna usługa językowa
 Najbardziej podstawowa usługa językowa zawiera następujące dwa obiekty:

- *Usługa języka* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejs. Usługa języka zawiera informacje o języku, w tym jego nazwę, rozszerzenia nazw plików, menedżera okien kodu i colorizer.

- *Koloryzator* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs.

  Poniższy rysunek koncepcyjny przedstawia model usługi języka podstawowego.

  ![Grafika przedstawiająca model usługi językowej](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Podstawowy model usługi językowej

  Okno dokumentu obsługuje *widok dokumentu* edytora, w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tym przypadku edytora podstawowego. Widok dokumentu i bufor tekstu są własnością edytora. Obiekty te [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] działają za pośrednictwem okna dokumentu specjalistycznego o nazwie *okno kodu*. Okno kodu znajduje się <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> w obiekcie, który jest tworzony i kontrolowany przez IDE.

  Po załadowaniu pliku z danym rozszerzeniem edytor lokalizuje usługę języka skojarzoną z tym rozszerzeniem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> i przekazuje do niego okno kodu, wywołując metodę. Usługa języka zwraca *menedżera okien kodu*, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> który implementuje interfejs.

  Poniższa tabela zawiera omówienie obiektów w modelu.

| Składnik | Obiekt | Funkcja |
|------------------| - | - |
| Bufor tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Strumień tekstu unicode odczytu/zapisu. Tekst może używać innych kodowania. |
| Okno Kod | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Okno dokumentu zawierające co najmniej jeden widok tekstu. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest w trybie interfejsu wielu dokumentów (MDI), okno kodu jest elementem podrzędnym MDI. |
| Widok tekstu | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Okno, które umożliwia użytkownikowi nawigację i wyświetlanie tekstu za pomocą klawiatury i myszy. Widok tekstu jest wyświetlany użytkownikowi jako edytor. Widoki tekstu można używać w zwykłych oknach edytora, w oknie Dane wyjściowe i w oknie Natychmiastowy. Ponadto można skonfigurować jeden lub więcej widoków tekstu w oknie kodu. |
| Menedżer tekstu | Zarządzane przez <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługę, z której <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> można uzyskać wskaźnik | Składnik, który przechowuje wspólne informacje współużytkowane przez wszystkie składniki opisane wcześniej. |
| Usługa językowa | Wdrożenie zależne; Implementuje<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Obiekt, który zapewnia edytorowi informacje specyficzne dla języka, takie jak wyróżnianie składni, uzupełnianie instrukcji i dopasowywanie nawiasów klamrowych. |

## <a name="see-also"></a>Zobacz też
- [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)
