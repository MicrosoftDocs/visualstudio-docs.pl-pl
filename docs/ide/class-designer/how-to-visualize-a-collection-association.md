---
title: 'Porady: wizualizacja skojarzeń kolekcji (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ba237b9c763421287e3878a6a98f59032bfd092
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590777"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Jak: Wizualizacja skojarzenia kolekcji w Projektancie klas

Właściwości i pola, które są kolekcje innych typów mogą być wyświetlane na diagramie klasy jako skojarzenia kolekcji. W przeciwieństwie do zwykłego skojarzenia, które wyświetla pole lub właściwość jako wiersz łączący klasę posiadającą z typem pola, skojarzenie kolekcji jest wyświetlane jako wiersz łączący klasę posiadającą z zebranym typem.

## <a name="to-create-a-collection-association"></a>Aby utworzyć skojarzenie kolekcji

1. W kodzie utwórz właściwość lub pole, którego typ jest sam w sobie kolekcją silnie typizowanej.

2. Na diagramie klasy rozwiń klasę tak, aby wyświetlane były właściwości i pola.

3. W klasie kliknij prawym przyciskiem myszy pole lub właściwość i wybierz polecenie **Pokaż jako skojarzenie kolekcji**.

Właściwość lub pole jest wyświetlane jako wiersz skojarzenia łączący się z typem zebranych.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie skojarzeń między typami](how-to-create-associations-between-types.md)
- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
