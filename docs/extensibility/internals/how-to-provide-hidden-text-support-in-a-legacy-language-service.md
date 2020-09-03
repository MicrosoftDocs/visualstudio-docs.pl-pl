---
title: Zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707929"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Instrukcje: zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej
Oprócz regionów konspektu można tworzyć ukryte regiony tekstowe. Ukryte regiony tekstu mogą być sterowane przez klienta lub kontrolowane przez Edytor i służą do całkowitego ukrywania regionu tekstu. Edytor wyświetla ukryty region jako poziome linie. Przykładem jest widok **tylko skrypt** w edytorze html.

## <a name="to-implement-a-hidden-text-region"></a>Aby zaimplementować ukryty obszar tekstu

1. Wywołaj metodę `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , przekazanie wskaźnika dla danego buforu tekstu. Określa, czy dla buforu istnieje już Ukryta sesja tekstu.

3. Jeśli taki już istnieje, nie musisz tworzyć jednego i zwracany jest wskaźnik do istniejącego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu. Użyj tego wskaźnika, aby wyliczyć i utworzyć ukryte regiony tekstowe. W przeciwnym razie Zadzwoń <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do tworzenia sesji tekstu ukrytego dla buforu.

     Zwracany jest wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu.

    > [!NOTE]
    > Po wywołaniu można `CreateHiddenTextSession` określić klienta tekstu ukrytego (czyli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). Klient tekstu ukrytego powiadamia użytkownika, gdy ukryty lub zwinięty tekst jest rozwinięty lub zwijany.

4. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> , aby dodać jeden lub więcej nowych regionów konspektu, określając następujące informacje w `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> parametrze ():

    1. Określ wartość `hrtConcealed` w `iType` składowej <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury, aby wskazać, że tworzysz ukryty region, a nie region konspektu.

        > [!NOTE]
        > Gdy ukrywane regiony są ukryte, Edytor automatycznie wyświetla linie wokół ukrytych regionów, aby wskazać ich obecność.

    2. Określ, czy region jest kontrolowany przez klienta czy w edytorze w `dwBehavior` składowej <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Twoja implementacja inteligentnego tworzenia konspektu może zawierać kombinację konspektu i ukrytych regionów tekstu, które są kontrolowane przez klienta.
