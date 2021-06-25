---
title: Wybór obiektów kontekstu | Microsoft Docs
description: Dowiedz się więcej na temat wewnętrznych informacji o tym, jak Visual Studio IDE używa obiektu kontekstu wyboru globalnego do określenia, co powinno być wyświetlane w idee.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c97108eaba426a4def4c1052d3adc7348eb88b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898490"
---
# <a name="selection-context-objects"></a>Obiekty kontekstu wyboru
Zintegrowane środowisko projektowe (IDE) używa obiektu kontekstu wyboru globalnego, aby określić, co powinno być [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wyświetlane w środowisku IDE. Każde okno w idee może mieć własny obiekt kontekstu wyboru wypychany do kontekstu wyboru globalnego. Ide aktualizuje kontekst wyboru globalnego wartościami z okna, gdy to okno ma fokus. Aby uzyskać więcej informacji, zobacz [Opinia dla użytkownika.](../../extensibility/internals/feedback-to-the-user.md)

 Każda ramka okna lub witryna w idee ma usługę o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Obiekt utworzony przez pakiet VSPackage, który znajduje się w ramce okna, musi wywołać metodę , aby `QueryService` uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu.

 Okna ramowe mogą chronić fragmenty informacji o kontekście wyboru przed propagacjami do globalnego kontekstu wyboru podczas ich rozpoczynania. Ta możliwość jest przydatna w przypadku okien narzędzi, które mogą wymagać pustego zaznaczenia.

 Modyfikowanie kontekstu wyboru globalnego wyzwala zdarzenia, które pakiet VSPackages może monitorować. Pakiet VSPackages może wykonywać następujące zadania, implementując `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfejsy i :

- Zaktualizuj aktualnie aktywny plik w hierarchii.

- Monitoruj zmiany niektórych typów elementów. Jeśli na przykład pakiet VSPackage  używa specjalnego okna Właściwości,  możesz monitorować zmiany w aktywnym oknie Właściwości i w razie potrzeby ponownie uruchamiać pakiet.

  W poniższej sekwencji przedstawiono typowy przebieg śledzenia wyboru.

1. Ide pobiera kontekst wyboru z nowo otwartego okna i umieszcza go w kontekście wyboru globalnego. Jeśli kontekst wyboru używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, te informacje nie są propagowane do kontekstu globalnego. Aby uzyskać więcej informacji, zobacz [Opinia dla użytkownika.](../../extensibility/internals/feedback-to-the-user.md)

2. Zdarzenia powiadomień są rozgłaszane do dowolnego pakietu VSPackage, który je zażądał.

3. Pakiet VSPackage działa na odbierane zdarzenia przez wykonywanie działań, takich jak aktualizowanie hierarchii, ponowne aktywowanie narzędzia lub inne podobne zadania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Typy projektów](../../extensibility/internals/project-types.md)
