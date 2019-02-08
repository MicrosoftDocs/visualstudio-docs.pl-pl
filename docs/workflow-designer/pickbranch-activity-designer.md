---
title: Projektant przepływu pracy — PickBranch, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6c452cb4fd5b8a343473204c2b2bee614383ebb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922059"
---
# <a name="pickbranch-activity-designer"></a>PickBranch, projektant działań

<xref:System.Activities.Statements.PickBranch> Zapewnia oparte na zdarzeniach ścieżką wykonywania w ramach <xref:System.Activities.Statements.Pick> działanie, które mogą być wyzwalane przez zdarzenia przychodzącego.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> obiekty są zawarte w <xref:System.Activities.Statements.Pick.Branches%2A> zbiór <xref:System.Activities.Statements.Pick> działania. Każdy <xref:System.Activities.Statements.PickBranch> znajduje się w gałęzi <xref:System.Activities.Statements.Pick> aktywności i mogą być wykonywane ze względu na niektóre zdarzenia przychodzące, która służy jako wyzwalacz. W ten sposób Workflow Designer udostępnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać Projektanta wybierz działanie

Dostęp do **PickBranch** projektanta w **przepływ sterowania** kategorii **przybornika**.

Dwa puste <xref:System.Activities.Statements.PickBranch> obiektów za pomocą wyświetlania nazw **Branch1** i **Branch2** są domyślnie tworzone jako elementy <xref:System.Activities.Statements.Pick> działania podczas **wybierz** Projektant działań początkowo zostało porzucone do projektanta przepływów pracy. Te odpowiednich <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości mogą być edytowane w **PickBranch** nagłówka projektanta lub w ramach **właściwości** okna dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> obiekty do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie **PickBranch** projektanta z **przybornika**, lub za pomocą menu kliknij prawym przyciskiem myszy w ramach **wybierz** powierzchni projektu:

- **PickBranch** Projektant <xref:System.Activities.Statements.PickBranch> kiedy zostanie przeciągnięty z **przybornika** i upuścić na jednej z gałęzi **wybierz** projektanta działań na Powierzchni projektanta przepływu pracy. Nowy <xref:System.Activities.Statements.PickBranch> obiektów, które można umieścić wewnątrz <xref:System.Activities.Statements.Pick> projektanta w lewo lub prawo do wszystkich istniejących <xref:System.Activities.Statements.PickBranch> elementów znajdujących się już w kolekcji. Podczas przeciągania **PickBranch** projektanta na **wybierz** projektanta za pomocą myszy **wybierz** projektanta używa pionowy pasek niebieski szare, aby wskazać miejsce <xref:System.Activities.Statements.PickBranch> jest dodawany do umieszczenia danego myszy.

- Kliknij prawym przyciskiem myszy **wybierz** Projektant działań (, ale nie w obrębie **PickBranch** designer) do uzyskania menu kontekstowe i wybierz **utwórz gałąź** Aby dodać nowy <xref:System.Activities.Statements.PickBranch>. Należy zauważyć, że nowy <xref:System.Activities.Statements.PickBranch> zostanie dodany do istniejącego po prawej stronie <xref:System.Activities.Statements.PickBranch> obiekty w **wybierz** projektanta.

**PickBranch** projektanta można rozszerzyć, aby wyświetlić **wyzwalacza** i **akcji** pola lub zwinięte, klikając double daszka po prawej stronie ich nagłówki. Edytuj <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A> każdego <xref:System.Activities.Statements.PickBranch> upuszczając działań na **wyzwalacza** i **akcji** pola ich twórców.

<xref:System.Activities.Statements.PickBranch> Obiekty w <xref:System.Activities.Statements.Pick.Branches%2A> zbiór <xref:System.Activities.Statements.Pick> obiektów, można zmienić kolejności, przeciągając i upuszczając je do nowej lokalizacji w ramach **wybierz** projektanta. **Wybierz** projektanta używa pionowy pasek niebieski szare, aby wskazać miejsce <xref:System.Activities.Statements.PickBranch> jest dodawany do umieszczenia danego myszy.

Istnieją dwa sposoby, aby usunąć <xref:System.Activities.Statements.PickBranch>:

- Wybierz **PickBranch** projektanta i usuń go.
- Wybierz **PickBranch** projektanta, kliknij prawym przyciskiem myszy uzyskać menu kontekstowe i wybierz **Usuń**.

Pamiętaj o wybraniu **PickBranch** projektanta, jak wybór jednego z działań wewnątrz jego **wyzwalacza** lub **akcji** pola przez pomyłkę spowoduje usunięcie jednej z tych działań i nie <xref:System.Activities.Statements.PickBranch> obiektu.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Właściwości PickBranch w Projektancie przepływu pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.PickBranch> właściwości i opisuje sposób używania ich w Projektancie przepływu pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Przyjazna nazwa wyświetlana w nagłówku **PickBranch** projektanta. Wartość domyślna to gałąź.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Prawda|Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> akcji, które może wywołać <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Action%2A> , jest wykonywany, jeśli wyzwolony.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)