---
title: 'Instrukcje: zmienianie przestrzeni nazw języka specyficznego dla domeny'
ms.date: 10/31/2018
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, namespace
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ff7c73694cb53f7fbea21514feeaab4abce3f29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542678"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Instrukcje: zmienianie przestrzeni nazw języka specyficznego dla domeny

Można zmienić przestrzeń nazw języka specyficznego dla domeny. Wprowadź zmiany w **Eksploratorze DSL**, we właściwościach projektu pakietu DSL i w informacjach o zestawie.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeń nazw języka specyficznego dla domeny

1. W **Eksploratorze DSL**wybierz węzeł **DSL** .

2. W oknie **Właściwości** Zmień właściwość **przestrzeń nazw** .

3. Zapisz rozwiązanie i Przekształć szablony.

4. W menu **projekt** wybierz polecenie **Właściwości DSL**.

   Pojawią się właściwości projektu.

5. Wybierz kartę **aplikacja** .

6. Zmień **domyślną właściwość Namespace** na nową nazwę przestrzeni nazw.

7. Jeśli chcesz również zmienić nazwę zestawu, Zmień **Właściwość Nazwa zestawu.**

8. Jeśli zmieniono nazwę zestawu, Otwórz DslPackage\Package.tt i zaktualizuj ten wiersz:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Jeśli Zapisano kod niestandardowy, pamiętaj o zmianie przestrzeni nazw i odwołań do klas w plikach kodu.

10. Zresetuj wystąpienie eksperymentalne programu Visual Studio.

    1. Usuń **\Users \\ **_{name}_**\AppData\Local\Microsoft\VisualStudio \\ \* **.

    2. W menu **Start** systemu Windows wybierz kolejno pozycje **Wszystkie programy**  >  **Microsoft Visual Studio 2010 zestaw**  >  **narzędzi**SDK  >  **Zresetuj wystąpienie eksperymentalne**.

11. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**.

## <a name="see-also"></a>Zobacz też

[Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)