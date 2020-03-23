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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61b598505ad465ec9086102b9e16e96cb7aa8275
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590387"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Jak: Tworzenie skojarzeń między typami w Projektancie klas

Wiersze skojarzenia w **Projektancie klas** pokazują, jak klasy na diagramie są powiązane. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.

Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)

> [!NOTE]
> **Projektant klas** obsługuje tylko skojarzenia jednokierunkowe.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy

1. W przyborniku w obszarze **Projektant klas**wybierz pozycję **Skojarzenie**.

2. Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.

     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.

## <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia

Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.

Alternatywnie wykonaj następujące kroki:

1. Zaznacz kształt zawierający właściwość, która jest wyświetlana jako skojarzenie.

   Kształt uzyskuje fokus, a jego elementy członkowskie są wyświetlane w oknach **Szczegóły klasy** i **Właściwości.**

2. W oknie **Szczegóły klasy** lub **Właściwości** edytuj pole nazwy dla tej właściwości i naciśnij klawisz **Enter**.

   Nazwa jest aktualizowana w oknie **Szczegóły klasy,** w wierszu skojarzenia, w oknie **Właściwości** i w kodzie.

## <a name="see-also"></a>Zobacz też

- [Jak: Zmiana notacji elementu członkowskiego i notacji skojarzenia](how-to-change-between-member-notation-and-association-notation.md)
