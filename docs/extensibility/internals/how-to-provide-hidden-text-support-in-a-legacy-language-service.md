---
title: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej
description: Dowiedz się, jak zapewnić obsługę tekstu ukrytego w starszej wersji usługi językowej, dodając regiony tekstu ukrytego kontrolowane przez edytor lub kontrolowane przez klienta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31c62f50cfff8662c543d24dceabdb429a9b9b05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901789"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>How to: Provide hidden text support in alegacy language service (Jak zapewnić obsługę tekstu ukrytego w starszej wersji usługi językowej)
Oprócz konspektu regionów można tworzyć regiony tekstu ukrytego. Ukryte obszary tekstu mogą być kontrolowane przez klienta lub edytora i są używane do całkowitego ukrycia regionu tekstu. Edytor wyświetla ukryty region jako linie poziome. Przykładem jest widok Tylko skrypt **w** edytorze HTML.

## <a name="to-implement-a-hidden-text-region"></a>Aby zaimplementować obszar tekstu ukrytego

1. Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , przekazując wskaźnik dla danego buforu tekstowego. Określa, czy istnieje już sesja ukrytego tekstu dla buforu.

3. Jeśli już istnieje, nie trzeba go tworzyć i jest zwracany wskaźnik <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> do istniejącego obiektu. Ten wskaźnik umożliwia wyliczanie i tworzenie ukrytych regionów tekstu. W przeciwnym razie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> wywołaj wywołanie , aby utworzyć ukrytą sesję tekstową dla buforu.

     Jest zwracany <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do obiektu .

    > [!NOTE]
    > Podczas wywołania `CreateHiddenTextSession` można określić ukrytego klienta tekstowego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). Klient tekstu ukrytego powiadamia, gdy ukryty tekst lub zwijanie zostanie rozwinięte lub zwinięte przez użytkownika.

4. Wywołaj wywołanie , aby dodać jeden lub więcej nowych regionów konspektu na raz, określając następujące informacje w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> `reHidReg` parametrze ( <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ):

    1. Określ wartość w składowej struktury, aby wskazać, że tworzysz ukryty region, a nie region `hrtConcealed` `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> konturu.

        > [!NOTE]
        > Gdy regiony ukryte są ukryte, edytor automatycznie wyświetla linie wokół ukrytych regionów, aby wskazać ich obecność.

    2. Określ, czy region jest kontrolowany przez klienta, czy kontrolowany przez edytor w `dwBehavior` członkach <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Implementacja inteligentnego konspektu może zawierać kombinację konspektu kontrolowanego przez edytor i klienta oraz ukrytych regionów tekstu.
