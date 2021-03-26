---
title: Obiekty kontekstu wyboru | Microsoft Docs
description: Dowiedz się więcej na temat wewnętrznych informacji o tym, jak środowisko IDE programu Visual Studio używa globalnego obiektu kontekstu wyboru, aby określić, co powinno być wyświetlane w IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca6239264ca1fa42edb0b73e8a96f523cb450857
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080843"
---
# <a name="selection-context-objects"></a>Obiekty kontekstu wyboru
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Zintegrowane środowisko programistyczne (IDE) używa obiektu kontekstu globalnego wyboru, aby określić, co powinno być wyświetlane w środowisku IDE. Każde okno w IDE może mieć własny obiekt kontekstu zaznaczenia wypychany do globalnego kontekstu wyboru. IDE aktualizuje kontekst zaznaczenia globalnego z wartościami z okna, gdy to okno ma fokus. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).

 Wszystkie ramki okna lub lokacje w IDE mają usługę o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Obiekt utworzony przez pakietu VSPackage, który znajduje się w ramce okna, musi wywołać metodę, `QueryService` Aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu.

 Okna ramowe mogą zachować propagowanie części informacji kontekstowych zaznaczenia z globalnego kontekstu wyboru po ich uruchomieniu. Ta możliwość jest przydatna w przypadku okien narzędzi, które mogą być uruchamiane z pustym wyborem.

 Modyfikowanie kontekstu globalnego wyboru wyzwala zdarzenia, które pakietów VSPackage może monitorować. Pakietów VSPackage mogą wykonywać następujące zadania przez implementację `IVsTrackSelectionEx` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfejsy:

- Zaktualizuj aktualnie aktywny plik w hierarchii.

- Monitoruj zmiany w niektórych typach elementów. Na przykład jeśli pakietu VSPackage korzysta z okna **Właściwości** specjalnych, można monitorować zmiany w oknie aktywne **Właściwości** i ponownie uruchamiać w razie potrzeby.

  Poniższa sekwencja przedstawia typowy kurs śledzenia wyboru.

1. IDE Pobiera kontekst zaznaczenia z nowo otwartego okna i umieszcza go w globalnym kontekście wyboru. Jeśli kontekst wyboru używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, te informacje nie są propagowane do kontekstu globalnego. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).

2. Zdarzenia powiadomień są emitowane do dowolnych pakietu VSPackage, które zażądały.

3. Pakietu VSPackage działa na zdarzeniach, które otrzymuje, wykonując działania, takie jak aktualizowanie hierarchii, ponowne aktywowanie narzędzia lub inne podobne zadania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Typy projektów](../../extensibility/internals/project-types.md)
