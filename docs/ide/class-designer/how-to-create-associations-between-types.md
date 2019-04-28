---
title: 'Instrukcje: Tworzenie skojarzeń między typami (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 723d1565dae55852829daf0038201d0c8685b3ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975388"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Instrukcje: Tworzenie skojarzeń między typami w Projektancie klas

Skojarzenie wierszy w **projektanta klas** pokazują, w jaki sposób są powiązane klas na diagramie. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.

Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)

> [!NOTE]
> **Projektant klasy** obsługuje tylko jednokierunkowe skojarzenia.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy

1. W przyborniku w obszarze **projektanta klas**, wybierz opcję **skojarzenie**.

2. Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.

     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.

## <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia

Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.

Alternatywnie wykonaj następujące kroki:

1. Wybierz kształt, który zawiera właściwość, która jest wyświetlana jako skojarzenie.

   Kształt uzyskuje fokus i jego składowe są prezentowane w **szczegóły klasy** i **właściwości** systemu windows.

2. W obu **szczegóły klasy** lub **właściwości** okna, wyedytuj pole nazwy dla tej właściwości i naciśnij klawisz **Enter**.

   Nazwa jest aktualizowana w **szczegóły klasy** okna na skojarzenie wiersz w **właściwości** okna, a w kodzie.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zmiana między notacją składowych i notacją skojarzeń](how-to-change-between-member-notation-and-association-notation.md)
