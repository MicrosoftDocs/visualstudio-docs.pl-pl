---
title: 'Instrukcje: zapewnianie rozszerzonej obsługi konspektu w starszej wersji usługi językowej | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837120"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dostępne są dwie opcje rozszerzania obsługi konspektu dla języka poza obsługę polecenia **Zwiń do definicji** . Można dodać regiony konspektu, które są kontrolowane przez Edytor, i dodawać regiony konspektu sterowane przez klienta.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Dodawanie regionów konspektu kontrolowanych przez Edytor  
 Użyj tej metody, aby utworzyć region konspektu, a następnie pozwól edytorowi obsłużyć, czy region jest rozwinięty, zwinięty i tak dalej. Z dwóch opcji zapewnienia obsługi konspektu, ta opcja jest najmniej niezawodna. W przypadku tej opcji utworzysz nowy region konspektu dla określonego zakresu tekstu przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Po utworzeniu tego regionu jego zachowanie jest kontrolowane przez Edytor. Aby zaimplementować regiony konspektu kontrolowane przez Edytor, należy wykonać poniższą procedurę.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowany przez Edytor  
  
1. Wywołanie `QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .  
  
2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , przekazanie wskaźnika dla danego buforu tekstu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu w buforze.  
  
3. Zadzwoń <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .  
  
4. Wywołaj, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Aby dodać jeden lub więcej nowych regionów konspektu jednocześnie.  
  
     Ta metoda pozwala określić zakres tekstu do konturu, czy istniejące regiony konspektu są usuwane lub zachowywane oraz czy region konspektu jest domyślnie rozwinięty, czy zwinięty.  
  
## <a name="adding-client-controlled-outline-regions"></a>Dodawanie regionów konspektu sterowanych przez klienta  
 To podejście służy do implementowania funkcji kontroli klienta (lub inteligentnych), takich jak używane przez [!INCLUDE[csprcs](../../includes/csprcs-md.md)] usługi i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Usługa językowa, która zarządza własnymi konspektami, monitoruje zawartość bufora tekstu w celu zniszczenia starych regionów konspektu, gdy stają się nieprawidłowe i w razie potrzeby tworzy nowe regiony konspektu.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowany przez klienta  
  
1. Wywołaj metodę `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .  
  
2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , przekazanie wskaźnika dla danego buforu tekstu. Określa, czy dla buforu istnieje już Ukryta sesja tekstu.  
  
3. Jeśli sesja tekstowa już istnieje, nie trzeba jej tworzyć i zostanie zwrócony wskaźnik do istniejącego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu. Użyj tego wskaźnika, aby wyliczyć i utworzyć regiony konspektu. W przeciwnym razie Zadzwoń <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do tworzenia sesji tekstu ukrytego dla buforu. Zwracany jest wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu.  
  
    > [!NOTE]
    > Po wywołaniu można <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> określić klienta tekstu ukrytego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> obiektu). Ten klient powiadamia użytkownika, gdy ukryty lub zwinięty region tekstu ukrytego lub konspektu.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Struktura wywołania) parametr: Określ wartość <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> w `iType` składowej <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, aby wskazać, że tworzysz region konspektu, a nie region ukryty. Określ, czy region jest kontrolowany przez klienta czy w edytorze w `dwBehavior` składowej <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Implementacja inteligentnego tworzenia konspektu może zawierać kombinację regionów konspektu, które są kontrolowane przez klienta. Określ tekst transparentu wyświetlany, gdy region konspektu jest zwinięty, na przykład "...", w `pszBanner` elemencie członkowskim <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Domyślny tekst transparentu edytora dla ukrytego regionu to "...".
