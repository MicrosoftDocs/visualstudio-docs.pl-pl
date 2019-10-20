---
title: Błędy Projektanta klas
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2fe684f4b10e3570e96a88c34d1e1c08c7388da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631910"
---
# <a name="class-designer-errors"></a>Błędy Projektanta klas

**Projektant klas** nie śledzi lokalizacji plików źródłowych, dlatego zmodyfikowanie struktury projektu lub przeniesienie plików źródłowych w projekcie może spowodować, że **Projektant klas** utratę śledzenia typu, na przykład, że często modyfikujesz typ źródła typedef, klasy bazowe i typy skojarzeń. Może zostać wyświetlony błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Aby rozwiązać ten problem, przeciągnij zmodyfikowany lub ponownie zlokalizowany kod źródłowy do diagramu klas, aby go wyświetlić.

## <a name="resources"></a>Resources

Pomoc dotyczącą innych błędów i ostrzeżeń można znaleźć w następujących zasobach:

- [Współpraca z kodem C++ wizualizacji](working-with-visual-cpp-code.md) zawiera informacje dotyczące rozwiązywania problemów z wyświetlaniem C++ w diagramie klas.
- [Forum Projektant klas programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) zawiera Forum dotyczące pytań dotyczących **Projektant klas**.

## <a name="see-also"></a>Zobacz także

- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
