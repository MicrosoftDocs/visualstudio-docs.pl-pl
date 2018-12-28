---
title: 'Projektant przepływu pracy — jak: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a486183b9f8c2f8a41b888d32cbc4113d25e51c8
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684629"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy

Przepływy pracy są definiowane zgodnie z XAML. Reprezentacja interfejsu użytkownika przepływu pracy jest oparty na drzewie XAML definiowanie przepływu pracy. Środowisko debugowania jest podobne do debugowania przepływów pracy w Projektancie przepływu pracy. Na przykład podczas debugowania XAML, zmienne lokalne, czujki i wątki w systemie windows działają tak samo jak w Projektancie przepływu pracy debugowania. Ponadto wyświetlanie stosu wywołań podczas debugowania XAML jest liniowej hierarchiczny widok przepływ wykonania przepływu pracy.

> [!NOTE]
> XAML dla przepływu pracy znajduje się w tym samym zestawie jako działania, zestawu część nazwy klas nie są uwzględniane. Bez tej części nazwy klas (działanie) XAML nie można załadować w czasie wykonywania. Nie zaleca się zdefiniowanie działania w tej samej przestrzeni nazw jako głównej projektu; w przeciwnym razie XAML będzie trzeba ręcznie modyfikować po edycji w projektancie.

## <a name="to-debug-workflow-xaml"></a>Aby debugować przepływ pracy XAML

1.  Otwórz projekt przepływu pracy lub działania w programie Visual Studio.

2.  Ustawianie punktu przerwania działania lub działania, który chcesz debugować, zgodnie z opisem w [jak: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Kliknij prawym przyciskiem myszy plik .xaml, który zawiera definicję przepływu pracy i wybierz **Wyświetl kod**. Widoczne będą wyświetlane w tym samym wierszu co deklaracja elementu XAML działanie, które można ustawić punkt przerwania w w widoku Projekt punktu przerwania.

4.  Wywoływanie debugera, zgodnie z opisem w [debugowania przepływów pracy](debugging-workflows-with-the-workflow-designer.md).

5.  Podczas wykonywania kodu osiągną jeden z punktów przerwania, zostanie wyróżniony element XAML skojarzone z tego punktu przerwania. Aby przejść do następnego punktu przerwania, należy użyć **F10** lub **F11** klucza.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debugowanie przepływów pracy](debugging-workflows-with-the-workflow-designer.md)