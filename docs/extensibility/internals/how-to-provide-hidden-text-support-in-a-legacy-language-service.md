---
title: Zapewnianie obsługi ukrytego tekstu w starszej usłudze językowej
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707929"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Jak: Zapewnienie obsługi ukrytego tekstu w starszej usłudze językowej
Oprócz regionów konspektu można tworzyć ukryte obszary tekstowe. Ukryte regiony tekstu mogą być kontrolowane przez klienta lub kontrolowane przez edytor i są używane do całkowitego ukrycia regionu tekstu. Edytor wyświetla ukryty obszar jako linie poziome. Przykładem tego jest widok **Tylko skrypt** w edytorze HTML.

## <a name="to-implement-a-hidden-text-region"></a>Aby zaimplementować obszar tekstu ukrytego

1. Zadzwoń `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>do .

     Spowoduje to powrót <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>wskaźnika do .

2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przechodząc w wskaźnik dla danego buforu tekstu. Określa to, czy sesja ukrytego tekstu już istnieje dla buforu.

3. Jeśli jeden już istnieje, to nie trzeba go utworzyć i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> zwracany jest wskaźnik do istniejącego obiektu. Ten wskaźnik służy do wyliczanie i tworzenie obszarów tekstu ukrytego. W przeciwnym <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> razie wywołanie utworzenia ukrytej sesji tekstowej dla buforu.

     Zwracany jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> wskaźnik do obiektu.

    > [!NOTE]
    > Podczas wywoływania `CreateHiddenTextSession`można określić ukrytego klienta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>tekstowego (czyli ). Klient ukrytego tekstu powiadamia użytkownika, gdy ukryty tekst lub tworzenie obliczenia jest rozwinięty lub zwinięty przez użytkownika.

4. Wywołanie, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> aby dodać jeden lub więcej nowych regionów konspektu naraz, określając następujące informacje w parametrze `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>):

    1. Określ wartość `hrtConcealed` w `iType` człozie struktury, <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> aby wskazać, że tworzysz ukryty region, a nie region konspektu.

        > [!NOTE]
        > Gdy ukryte regiony są ukryte, edytor automatycznie wyświetla linie wokół ukrytych regionów, aby wskazać ich obecność.

    2. Określ, czy region jest kontrolowany przez `dwBehavior` klienta <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> lub kontrolowany przez edytor w elementach członkowskich struktury. Inteligentna implementacja konspektu może zawierać kombinację regionów konspektu i ukrytego tekstu kontrolowanego przez edytora i klienta.
