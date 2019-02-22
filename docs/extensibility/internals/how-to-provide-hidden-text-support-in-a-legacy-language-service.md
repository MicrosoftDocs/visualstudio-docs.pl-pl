---
title: 'Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df34e65eda5dd871dc62132059dce0ac75e4030f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612436"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Instrukcje: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej
Można utworzyć tekstu ukrytego regionach oprócz regionów konspektu. Regiony tekstu ukrytego mogą być kontrolowane przez klienta lub kontrolowane przez Edytor i są używane do całkowicie ukryć region tekstu. W edytorze są wyświetlane ukryty region jako poziome linie. Na przykład **tylko skrypt** widoku w edytorze HTML.


## <a name="to-implement-a-hidden-text-region"></a>Aby zaimplementować tekst ukryty region

1.  Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.

     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.

2.  Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnik do buforu danego tekstu. Określa, czy sesja ukryty tekst, który jest już istnieje dla buforu.

3.  Jeśli już istnieje, a następnie nie musisz utworzyć jeden, a wskaźnik do istniejących <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany. Za pomocą tego wskaźnika mógł wyliczyć i utworzyć regiony tekstu ukrytego. W przeciwnym razie wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do utworzenia sesji ukrytego tekstu dla buforu.

     Wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany.

    > [!NOTE]
    >  Gdy wywołujesz `CreateHiddenTextSession`, można określić klienta tekstu ukrytego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Klient tekstu ukrytego powiadamia tekstu ukrytego lub Tworzenie konspektu jest rozwinięta czy zwinięta przez użytkownika.

4.  Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> można dodać jeden lub więcej nowych konspektu regionów w czasie, określając następujące informacje w `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametr:

    1.  Określ wartość `hrtConcealed` w `iType` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, aby wskazać, tworzysz ukryty region, a nie z regionu konspektu.

        > [!NOTE]
        >  Po ukryte regiony są ukryte, w edytorze są wyświetlane na linie wokół ukryte obszary wskazanie ich obecności.

    2.  Określ, czy region jest kontrolowany przez klienta lub Edytor kontrolowane w `dwBehavior` członkowie <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentne implementacji konspektu może zawierać zarówno konspektu kontrolowane przez Edytor i klienta i tekst ukryty regionów.