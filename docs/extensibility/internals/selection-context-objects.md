---
title: Obiekty kontekstu zaznaczenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705511"
---
# <a name="selection-context-objects"></a>Obiekty kontekstu wyboru
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) używa obiektu kontekstu wyboru globalnego do określenia, co powinno być wyświetlane w IDE. Każde okno w IDE może mieć swój własny obiekt kontekstu zaznaczenia wypchnięty do kontekstu zaznaczenia globalnego. IDE aktualizuje kontekst wyboru globalnego z wartościami z okna, gdy to okno ma fokus. Aby uzyskać więcej informacji, zobacz [Opinie do użytkownika](../../extensibility/internals/feedback-to-the-user.md).

 Każda ramka okna lub lokacja <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>w IDE ma usługę o nazwie . Obiekt utworzony przez VSPackage, który znajduje się w `QueryService` ramce okna musi <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> wywołać metodę, aby uzyskać wskaźnik do interfejsu.

 Okna ramek mogą uniemożliwiać propagowanie części informacji kontekstowych zaznaczenia do kontekstu zaznaczenia globalnego po ich uruchomieniu. Ta możliwość jest przydatna w przypadku okien narzędzi, które mogą wymagać rozpoczęcia od pustego zaznaczenia.

 Modyfikowanie kontekstu zaznaczenia globalnego wyzwala zdarzenia, które vspackages można monitorować. VsPackages można wykonywać następujące zadania, implementując `IVsTrackSelectionEx` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfejsy:

- Zaktualizuj aktualnie aktywny plik w hierarchii.

- Monitorowanie zmian w niektórych typach elementów. Na przykład jeśli VSPackage używa specjalnego okna **Właściwości,** można monitorować zmiany w aktywnym oknie **Właściwości** i ponownie uruchomić swój, gdy jest to wymagane.

  Poniższa sekwencja przedstawia typowy przebieg śledzenia wyboru.

1. IDE pobiera kontekst wyboru z nowo otwartego okna i umieszcza go w kontekście zaznaczenia globalnego. Jeśli kontekst wyboru używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, informacje te nie są propagowane do kontekstu globalnego. Aby uzyskać więcej informacji, zobacz [Opinie do użytkownika](../../extensibility/internals/feedback-to-the-user.md).

2. Zdarzenia powiadomień są emitowane do dowolnego vspackage, który ich zażądał.

3. VSPackage działa na zdarzenia, które otrzymuje, wykonując działania, takie jak aktualizowanie hierarchii, ponowne aktywowanie narzędzia lub innych podobnych zadań.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)
