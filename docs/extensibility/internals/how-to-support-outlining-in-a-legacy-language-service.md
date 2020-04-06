---
title: 'Jak: Obsługa nakreślenia w starszej usłudze językowej | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707917"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Jak: Obsługa nakreślenia w starszej usłudze językowej
Tworzenie konspektów służy do rozwijania lub zwijania różnych obszarów tekstu. Sposób, w jaki jest używany sposób nakreślenia może być zdefiniowany inaczej przez różne języki. Aby uzyskać więcej informacji, zobacz [Tworzenie przedstawiające](../../ide/outlining.md).

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie wdrażania nakreślenia, zobacz [Przewodnik: Tworzenie nakreślenia](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

 Poniżej pokazano, jak obsługiwać to polecenie dla usługi języka.

## <a name="to-support-outlining"></a>Aby wspierać tworzenie

1. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> obiekt usługi języka.

2. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> bieżącego obiektu sesji konspektu, aby dodać nowe regiony konspektu.

## <a name="robust-programming"></a>Solidne programowanie
 Gdy użytkownik wybierze **Zwiń do definicji** w menu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> **Konspekt,** IDE wywołuje usługę języka.

 Gdy ta metoda jest wywoływana, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> IDE przekazuje w wskaźniku (wskaźnik do buforu tekstu) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (wskaźnik do bieżącej sesji przedstawiającej).

 Metodę można <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> wywołać dla wielu regionów konspektu, `rgOutlnReg` określając te regiony w parametrze. Parametr `rgOutlnReg` jest <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> strukturą. Ten proces umożliwia określenie różnych cech regionu ukrytego, takich jak czy określony region jest rozwinięty lub zwinięty.

> [!NOTE]
> Należy uważać na ukrywanie znaków nowej linii. Ukryty tekst powinien rozciągać się od początku pierwszego wiersza do ostatniego znaku ostatniego wiersza w przekroju, pozostawiając widoczny końcowy znak nowego wiersza.

## <a name="see-also"></a>Zobacz też
- [Jak: Zapewnienie obsługi ukrytego tekstu w starszej usłudze językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Jak: Zapewnienie rozszerzonej obsługi nakreślenia w starszej usłudze językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
