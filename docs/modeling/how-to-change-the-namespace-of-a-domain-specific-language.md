---
title: 'Instrukcje: Zmienianie przestrzeni nazw języka specyficznego dla domeny'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 68566324c77796df8ce952135c0752cbb16033a5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984967"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Instrukcje: Zmienianie przestrzeni nazw języka specyficznego dla domeny

Można zmienić przestrzeni nazw języka specyficznego dla domeny. Wprowadź zmiany w **Eksplorator DSL**, we właściwościach projektu Dsl pakietu oraz informacje o zestawie.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeni nazw języka specyficznego dla domeny

1. W **Eksplorator DSL**, wybierz opcję **Dsl** węzła.

2. W **właściwości** oknie zmiany **Namespace** właściwości.

3. Zapisywanie rozwiązania i przekształcania szablonów.

4. Na **projektu** menu, wybierz **właściwości Dsl**.

   Właściwości projektu są wyświetlane.

5. Wybierz **aplikacji** kartę.

6. Zmiana **domyślny obszar nazw** właściwości na nową nazwę przestrzeni nazw.

7. Jeśli chcesz także zmienić nazwę zestawu, zmień **właściwości nazwy zestawu.**

8. Jeśli zmieniono nazwę zestawu, otwórz DslPackage\Package.tt i zaktualizować ten wiersz:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Jeśli napisano kodu niestandardowego, upewnij się zmienić odwołania do przestrzeni nazw i klasy w plikach kodu.

10. Zresetuj wystąpienie eksperymentalne programu Visual Studio.

    1. Usuń **\Users\\**_{name}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. Na Windows **Start** menu, wybierz **wszystkie programy** > **Microsoft Visual Studio 2010 SDK** > **narzędzia**  >  **Zresetuj wystąpienie eksperymentalne**.

11. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="see-also"></a>Zobacz także

[Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)