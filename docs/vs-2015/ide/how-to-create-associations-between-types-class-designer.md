---
title: 'Instrukcje: tworzenie skojarzeń między typami (Projektant klas) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb46d3bf7096d0a7e14ce3926514d946d7536e2d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668115"
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Instrukcje: tworzenie skojarzeń między typami (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Linie skojarzenia w Konstruktorze klasy pokazują relacje klas na diagramie. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.

 Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)

> [!NOTE]
> Projektant klasy obsługuje tylko jednokierunkowe skojarzenia.

### <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy

1. W przyborniku w obszarze Projektant klas wybierz pozycję **skojarzenie**.

2. Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.

     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.

### <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia

- Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.

  \- lub-

1. Kliknij kształt, który zawiera właściwość, która jest wyświetlana jako skojarzenie.

     Kształt uzyskuje fokus, a jego składowe są prezentowane w oknie Szczegóły klasy i w oknie Właściwości.

2. W oknie Szczegóły klasy lub w oknie Właściwości, wyedytuj pole nazwy dla tej właściwości, a następnie naciśnij klawisz Enter.

     Nazwa zostanie zaktualizowana w oknie **Szczegóły klasy** , w wierszu skojarzenia, w okno właściwości i w kodzie.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Zmiana między notacją składowych i notacją skojarzeń (Projektant klas)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
