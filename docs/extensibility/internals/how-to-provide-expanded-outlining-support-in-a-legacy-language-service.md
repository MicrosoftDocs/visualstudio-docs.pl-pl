---
title: Zapewnienie obsługi klienta w usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707966"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Jak: Zapewnienie rozszerzonej obsługi nakreślenia w starszej usłudze językowej
Istnieją dwie opcje rozszerzania obsługi konspektów dla twojego języka poza obsługę polecenia **Zwiń do definicji.** Można dodawać regiony konspektu kontrolowane przez edytor i dodawać regiony konspektu kontrolowane przez klienta.

## <a name="adding-editor-controlled-outline-regions"></a>Dodawanie regionów konspektu kontrolowanych przez edytor
 Użyj tego podejścia, aby utworzyć region konspektu, a następnie zezwolić edytorowi na obsługę, czy region jest rozwinięty, zwinięty i tak dalej. Z dwóch opcji zapewniających obsługę nakreślenia ta opcja jest najmniej solidna. W przypadku tej opcji można utworzyć nowy obszar konspektu na określonym zakresie tekstu za pomocą programu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Po utworzeniu tego regionu jego zachowanie jest kontrolowane przez edytora. Poniższa procedura służy do implementowania regionów konspektu kontrolowanych przez edytora.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowany przez edytor

1. Wezwanie `QueryService` do<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Spowoduje to powrót <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>wskaźnika do .

2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przechodząc w wskaźnik dla danego buforu tekstu. Spowoduje to zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do obiektu dla buforu.

3. <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Zadzwoń, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> aby uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>wskaźnik do .

4. Wywołanie, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> aby dodać jeden lub więcej nowych regionów konspektu naraz.

     Ta metoda umożliwia określenie zakresu tekstu do konspektu, czy istniejące regiony konspektu są usuwane lub zachowywane oraz czy region konspektu jest domyślnie rozwinięty czy zwinięty.

## <a name="add-client-controlled-outline-regions"></a>Dodawanie regionów konspektu kontrolowanych przez klienta
 Użyj tego podejścia do zaimplementowania kontrolowanych przez klienta [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (lub inteligentnych) nakreślenia, takich jak używane przez usługi i języka. Usługa języka, która zarządza własnym konspektem monitoruje zawartość buforu tekstu w celu zniszczenia starych regionów konspektu, gdy staną się one nieprawidłowe i utworzyć nowe regiony konspektu w razie potrzeby.

### <a name="to-implement-a-client-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowany przez klienta

1. Zadzwoń `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>do . Spowoduje to powrót <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>wskaźnika do .

2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przechodząc w wskaźnik dla danego buforu tekstu. Określa to, czy sesja ukrytego tekstu już istnieje dla buforu.

3. Jeśli sesja tekstowa już istnieje, nie trzeba jej tworzyć, a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do istniejącego obiektu jest zwracany. Ten wskaźnik służy do wyliczanie i tworzenie regionów konspektu. W przeciwnym <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> razie wywołanie utworzenia ukrytej sesji tekstowej dla buforu. Zwracany jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do obiektu.

    > [!NOTE]
    > Podczas wywoływania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>można określić ukrytego klienta tekstowego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> (czyli obiektu). Ten klient powiadamia użytkownika, gdy ukryty tekst lub region konspektu zostanie rozwinięty lub zwinięty przez użytkownika.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Wywołanie struktury) parametr: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> Określ `iType` wartość <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> w człony struktury, aby wskazać, że tworzysz region konspektu, a nie ukryty region. Określ, czy region jest kontrolowany przez `dwBehavior` klienta <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> lub kontrolowany przez edytor w człowiecie. Inteligentna implementacja konspektu może zawierać kombinację regionów konspektu kontrolowanych przez edytora i klienta. Określ tekst transparentu, który jest wyświetlany po zwinięciu regionu `pszBanner` konspektu, na przykład "...", w członu <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Domyślny tekst transparentu edytora dla ukrytego regionu to "...".
