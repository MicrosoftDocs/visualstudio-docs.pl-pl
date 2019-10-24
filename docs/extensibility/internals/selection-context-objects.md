---
title: Obiekty kontekstu wyboru | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc4f0aad4dd3f28f28259d0ca439a0cda1a520d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723911"
---
# <a name="selection-context-objects"></a>Obiekty kontekstu wyboru
@No__t_0 zintegrowanego środowiska programistycznego (IDE) używa obiektu kontekstu globalnego wyboru, aby określić, co powinno być wyświetlane w IDE. Każde okno w IDE może mieć własny obiekt kontekstu zaznaczenia wypychany do globalnego kontekstu wyboru. IDE aktualizuje kontekst zaznaczenia globalnego z wartościami z okna, gdy to okno ma fokus. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).

 Wszystkie ramki okna lub lokacje w IDE mają usługę o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Obiekt utworzony przez pakietu VSPackage, który znajduje się w ramce okna, musi wywoływać metodę `QueryService`, aby uzyskać wskaźnik do interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

 Okna ramowe mogą zachować propagowanie części informacji kontekstowych zaznaczenia z globalnego kontekstu wyboru po ich uruchomieniu. Ta możliwość jest przydatna w przypadku okien narzędzi, które mogą być uruchamiane z pustym wyborem.

 Modyfikowanie kontekstu globalnego wyboru wyzwala zdarzenia, które pakietów VSPackage może monitorować. Pakietów VSPackage mogą wykonywać następujące zadania, implementując interfejsy `IVsTrackSelectionEx` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>:

- Zaktualizuj aktualnie aktywny plik w hierarchii.

- Monitoruj zmiany w niektórych typach elementów. Na przykład jeśli pakietu VSPackage korzysta z okna **Właściwości** specjalnych, można monitorować zmiany w oknie aktywne **Właściwości** i ponownie uruchamiać w razie potrzeby.

  Poniższa sekwencja przedstawia typowy kurs śledzenia wyboru.

1. IDE Pobiera kontekst zaznaczenia z nowo otwartego okna i umieszcza go w globalnym kontekście wyboru. Jeśli kontekst wyboru używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, te informacje nie są propagowane do kontekstu globalnego. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).

2. Zdarzenia powiadomień są emitowane do dowolnych pakietu VSPackage, które zażądały.

3. Pakietu VSPackage działa na zdarzeniach, które otrzymuje, wykonując działania, takie jak aktualizowanie hierarchii, ponowne aktywowanie narzędzia lub inne podobne zadania.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Typy projektów](../../extensibility/internals/project-types.md)