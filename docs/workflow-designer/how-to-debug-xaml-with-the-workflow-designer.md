---
title: 'Projektant przepływu pracy: Debuguj kod XAML'
description: Dowiedz się, w jaki sposób przepływy pracy są zdefiniowane w języku XAML i jak debugować kod XAML przy użyciu Projektant przepływu pracy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 78141b6f3c33903603d7cbb082eca6de55ee757c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971664"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy

Przepływy pracy są zdefiniowane w postaci języka XAML. Reprezentacja interfejsu użytkownika jest tworzona na podstawie drzewa XAML definiującego przepływ pracy. Środowisko debugowania jest podobne do debugowania przepływów pracy w Projektant przepływu pracy. Na przykład podczas debugowania XAML, okna lokalne, czujka i wątki działają tak samo, jak w Projektant przepływu pracy debugowanie. Ponadto widok stosu wywołań podczas debugowania XAML to hierarchiczny widok przepływu wykonywania przepływu pracy w oparciu o wiersz.

> [!NOTE]
> Jeśli kod XAML dla przepływu pracy znajduje się w tym samym zestawie co działania, część nazw klas nie jest uwzględniana. Bez tej części nazw klas (Activity) nie można załadować XAML w czasie wykonywania. Nie zaleca się definiowania działań w tej samej przestrzeni nazw co projekt główny; w przeciwnym razie kod XAML będzie musiał być edytowany ręcznie po edycji w projektancie.

## <a name="to-debug-workflow-xaml"></a>Aby debugować kod XAML przepływu pracy

1. Otwórz przepływ pracy lub projekt działania w programie Visual Studio.

2. Ustaw punkt przerwania działania lub działań, które chcesz debugować zgodnie z opisem w [instrukcje: ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Kliknij prawym przyciskiem myszy plik XAML, który zawiera definicję przepływu pracy, a następnie wybierz polecenie **Wyświetl kod**. Punkt przerwania jest wyświetlany w tym samym wierszu co Deklaracja elementu XAML działania, dla którego ustawisz punkt przerwania w widoku projektu.

4. Wywołaj debuger zgodnie z opisem w obszarze [przepływy pracy debugowania](debugging-workflows-with-the-workflow-designer.md).

5. Gdy wykonanie kodu osiągnie jeden z punktów przerwania, element XAML skojarzony z tym punktem przerwania zostanie wyróżniony. Aby przejść do następnego punktu przerwania, użyj klawisza **F10** lub **F11** .

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debugowania przepływów pracy](debugging-workflows-with-the-workflow-designer.md)
