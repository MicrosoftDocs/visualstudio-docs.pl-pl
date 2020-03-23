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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8b2c013a3e685a6071f4a12d63e3ca475051a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596518"
---
# <a name="class-designer-errors"></a>Błędy Projektanta klas

**Projektant klas** nie śledzi lokalizacji plików źródłowych, więc modyfikowanie struktury projektu lub przenoszenie plików źródłowych w projekcie może spowodować, że **Projektant klas** utracił śledzenie typu, Na przykład często modyfikuje typ źródłowy type typedef, klas podstawowych i typów skojarzeń. Może pojawić się błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Aby rozwiązać ten problem, przeciągnij zmodyfikowany lub przeniesiony kod źródłowy do diagramu klas ponownie, aby go wyświetlić.

## <a name="resources"></a>Zasoby

Pomoc dotyczącą innych błędów i ostrzeżeń można znaleźć w następujących zasobach:

- [Praca z kodem języka Visual C++](working-with-visual-cpp-code.md) zawiera informacje dotyczące rozwiązywania problemów z wyświetlaniem języka C++ na diagramie klasy.
- [Forum projektanta klas programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) zawiera forum pytań dotyczących **projektanta klas.**

## <a name="see-also"></a>Zobacz też

- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
