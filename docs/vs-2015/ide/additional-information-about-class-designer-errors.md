---
title: Dodatkowe informacje na temat błędów Projektant klas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a095cd909dcd4d378fddc91c9151cf28e34a8ee5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852209"
---
# <a name="additional-information-about-class-designer-errors"></a>Dodatkowe informacje na temat błędów w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas nie śledzi lokalizacji plików źródłowych, dlatego zmodyfikowanie struktury projektu lub przeniesienie plików źródłowych w projekcie może spowodować, że Projektant klas utraci śledzenie typu (szczególnie typ źródłowy typedef, klasy bazowe lub typy skojarzeń). Może zostać wyświetlony błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij ponownie zmodyfikowany lub zlokalizowany kod źródłowy do diagramu klas, aby go wyświetlić.

 Pomoc dotyczącą innych błędów i ostrzeżeń można znaleźć w następujących zasobach:

 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md) Zawiera informacje dotyczące rozwiązywania problemów z wyświetlaniem języka C++ w diagramie klas.

 [Forum Projektant klas programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1) Zawiera forum z pytaniami dotyczącymi Projektant klas.

## <a name="see-also"></a>Zobacz też
 [Projektowanie i wyświetlanie klas i typów](../ide/designing-and-viewing-classes-and-types.md)
