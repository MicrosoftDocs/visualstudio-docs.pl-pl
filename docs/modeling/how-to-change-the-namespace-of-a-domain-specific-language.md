---
title: 'Instrukcje: zmienianie przestrzeni nazw języka specyficznego dla domeny'
description: Zawiera informacje o sposobie zmiany przestrzeni nazw języka specyficznego dla domeny.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: a7b0de26fdc1a7982347a12c283a6aa73e9aad12
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809443"
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

[Słownik narzędzi języka specyficznego dla domeny](/previous-versions/bb126564(v=vs.100))