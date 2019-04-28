---
title: 'Instrukcje: Zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1b2fd8f3d7e4f3637957ef11c4acb20ba51261d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442675"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Instrukcje: Zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dostępne są dwie opcje do rozszerzania możliwości programu obsługi zwijania dla danego języka, poza obsługi **Zwiń do definicji** polecenia. Można Dodawanie regionów kontrolowane przez Edytor konturu i dodawanie regionów konspektu kontrolowane przez klienta.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Dodawanie regionów kontrolowane przez Edytor konspektu  
 Użyj tej metody, aby Tworzenie konspektu regionu, a następnie zezwolić na edytorowi obsługę czy region jest rozwinięta, zwinięte i tak dalej. Z dwóch opcji obsługi konspektu ta opcja jest najmniej niezawodne. Dla tej opcji, Utwórz nowy region konspektu przez określony fragment tekstu za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Po utworzeniu tego regionu jego zachowanie jest kontrolowana przez edytor. Użyj poniższej procedury do wdrożenia regiony konspektu kontrolowane przez edytor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Aby zaimplementować z regionu kontrolowane przez Edytor konspektu  
  
1. Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnik do buforu danego tekstu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu dla buforu.  
  
3. Wywołaj <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> dla wskaźnika do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> można dodać jeden lub więcej nowych konturu regiony na raz.  
  
     Ta metoda umożliwia określenie zakresu tekstu do konspektu, czy usunąć lub zachowane istniejących regionach konturu i tego, czy region konspektu jest rozwinięta, czy zwinięta domyślnie.  
  
## <a name="adding-client-controlled-outline-regions"></a>Dodawanie regionów konspektu kontrolowane przez klienta  
 Użyj tego podejścia do konspektu Implementowanie kontrolowane przez klienta (lub inteligentne), takich jak używanego przez [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] usług językowych. Usługa języka, która zarządza własną konspekt monitoruje zawartości buforu tekstowego, aby zniszczyć stary regionów konspektu, gdy staje się nieprawidłowy i utworzyć nowe regiony konspektu, zgodnie z potrzebami.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowane przez klienta  
  
1. Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnik do buforu danego tekstu. Określa, czy sesja ukryty tekst, który jest już istnieje dla buforu.  
  
3. Jeśli sesja tekst, który jest już istnieje, a następnie nie musisz utworzyć jeden, a wskaźnik do istniejących <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany. Za pomocą tego wskaźnika mógł wyliczyć i tworzenie konspektu regionów. W przeciwnym razie wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do utworzenia sesji ukrytego tekstu dla buforu. Wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany.  
  
    > [!NOTE]
    > Podczas wywoływania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, można określić klienta tekstu ukrytego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> obiektu). Ten klient powiadamia użytkownika, gdy tekstu ukrytego lub konspektu region jest rozwinięta czy zwinięta przez użytkownika.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> struktury) parametr: Określ wartość <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> w `iType` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, aby wskazać, tworzysz region konspektu, zamiast ukryty region. Określ, czy region jest kontrolowany przez klienta lub Edytor kontrolowane w `dwBehavior` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentne implementacji konspektu może zawierać kombinację regionów konspektu kontrolowane przez Edytor i klienta. Podaj tekst transparentu, który jest wyświetlane, gdy w Twoim regionie konspektu jest zwinięte, takie jak "..." w `pszBanner` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Edytor domyślny Baner tekst ukryty region jest "...".
