---
title: 'Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f453740e3a3ea3f70e76f104a8a79406a814dea0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089201"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Można utworzyć tekstu ukrytego regionach oprócz regionów konspektu. Regiony tekstu ukrytego mogą być kontrolowane przez klienta lub kontrolowane przez Edytor i są używane do całkowicie ukryć region tekstu. W edytorze są wyświetlane ukryty region jako poziome linie. Na przykład jest widok tylko skrypt w edytorze HTML.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-implement-a-hidden-text-region"></a>Aby zaimplementować tekst ukryty region  
  
1. Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnik do buforu danego tekstu. Określa, czy sesja ukryty tekst, który jest już istnieje dla buforu.  
  
3. Jeśli już istnieje, a następnie nie musisz utworzyć jeden, a wskaźnik do istniejących <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany. Za pomocą tego wskaźnika mógł wyliczyć i utworzyć regiony tekstu ukrytego. W przeciwnym razie wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do utworzenia sesji ukrytego tekstu dla buforu.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany.  
  
    > [!NOTE]
    >  Gdy wywołujesz `CreateHiddenTextSession`, można określić klienta tekstu ukrytego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Klient tekstu ukrytego powiadamia tekstu ukrytego lub Tworzenie konspektu jest rozwinięta czy zwinięta przez użytkownika.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> można dodać jeden lub więcej nowych konspektu regionów w czasie, określając następujące informacje w `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametr:  
  
    1. Określ wartość `hrtConcealed` w `iType` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, aby wskazać, tworzysz ukryty region, a nie z regionu konspektu.  
  
        > [!NOTE]
        >  Po ukryte regiony są ukryte, w edytorze są wyświetlane na linie wokół ukryte obszary wskazanie ich obecności.  
  
    2. Określ, czy region jest kontrolowany przez klienta lub Edytor kontrolowane w `dwBehavior` członkowie <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentne implementacji konspektu może zawierać zarówno konspektu kontrolowane przez Edytor i klienta i tekst ukryty regionów.
