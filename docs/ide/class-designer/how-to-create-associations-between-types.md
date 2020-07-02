---
title: 'Instrukcje: Tworzenie skojarzeń między typami (Projektant klas)'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 3cce893efaad5f2317b175391a2685cae7053e3c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770952"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Instrukcje: tworzenie skojarzeń między typami w Projektant klas

Linie skojarzenia w **Projektant klas** pokazują, jak są powiązane klasy w diagramie. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.

Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)

> [!NOTE]
> **Projektant klas** obsługuje tylko jednokierunkowe skojarzenia.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy

1. W przyborniku w obszarze **Projektant klas**wybierz pozycję **skojarzenie**.

2. Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.

     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.

## <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia

Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.

Alternatywnie wykonaj następujące kroki:

1. Wybierz kształt zawierający właściwość, która jest wyświetlana jako skojarzenie.

   Kształt uzyskuje fokus i jego składowe są wyświetlane w oknach **Szczegóły klasy** i **Właściwości** .

2. W oknie **Szczegóły klasy** lub **Właściwości** , edytuj pole Nazwa dla tej właściwości i naciśnij klawisz **Enter**.

   Nazwa zostanie zaktualizowana w oknie **Szczegóły klasy** , w wierszu skojarzenia, w oknie **Właściwości** i w kodzie.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: zmiana między notacją składowej i notacją skojarzenia](how-to-change-between-member-notation-and-association-notation.md)
