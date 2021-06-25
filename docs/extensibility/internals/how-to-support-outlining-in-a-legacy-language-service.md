---
title: 'How to: Support Outlining in a Legacy Language Service | Microsoft Docs'
description: Dowiedz się, jak zapewnić obsługę zwijania, rozwijania lub zwijania różnych regionów tekstu w starszej wersji usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 028d1a9aae21aae8c6368e4eea3820aabd200be6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901802"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>How to: Support outlining in alegacy language service ( How to: Support outlining in alegacy language service)
Zwijanie służy do rozwijania lub zwijania różnych regionów tekstu. Sposób, w jaki jest używany, można zdefiniować inaczej w różnych językach. Aby uzyskać więcej informacji, zobacz [Temat .](../../ide/outlining.md)

 Starsze usługi językowe są implementowane w ramach pakietów VSPackage, ale nowszą sposobem implementacji funkcji usługi językowej jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej na temat nowego sposobu implementowania kreślenia, zobacz [Przewodnik: opis](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Zalecamy jak najszybciej rozpocząć korzystanie z nowego interfejsu API edytora. Poprawi to wydajność usługi językowej i pozwoli korzystać z nowych funkcji edytora.

 Poniżej przedstawiono sposób obsługi tego polecenia dla usługi językowej.

## <a name="to-support-outlining"></a>Aby obsługiwać cytowanie

1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>Zaim implementuj w obiekcie usługi językowej.

2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> dla bieżącego obiektu konspektu sesji, aby dodać nowe regiony konspektu.

## <a name="robust-programming"></a>Niezawodne programowanie
 Gdy użytkownik wybierze pozycję **Zwiń do definicji** w menu **Zwijanie,** ide wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> usługę językową.

 Gdy ta metoda jest wywoływana, ide przekazuje wskaźnik (wskaźnik do bufora tekstowego) i (wskaźnik do bieżącej sesji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> linowania).

 Możesz wywołać metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> dla wielu regionów konspektu, określając te regiony w `rgOutlnReg` parametrze . Parametr `rgOutlnReg` jest <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> strukturą. Ten proces umożliwia określenie różnych cech ukrytego regionu, na przykład tego, czy dany region jest rozwinięty, czy zwinięty.

> [!NOTE]
> Należy zachować ostrożność podczas ukrywania znaków nowego wiersza. Tekst ukryty powinien być rozszerzany od początku pierwszego wiersza do ostatniego znaku ostatniego wiersza w sekcji, pozostawiając widoczny ostatni znak nowego wiersza.

## <a name="see-also"></a>Zobacz też
- [How to: Provide hidden text support in alegacy language service (Jak zapewnić obsługę tekstu ukrytego w starszej wersji usługi językowej)](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [How to: Provide expanded outlining support in alegacy language service (Jak zapewnić rozszerzoną obsługę liningu w starszej wersji usługi językowej)](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
