---
title: 'Instrukcje: zmienianie przestrzeni nazw języka specyficznego dla domeny'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653763"
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

    1. Usuń **\users \\** _{name}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**.

    2. W menu **Start** systemu Windows wybierz kolejno pozycje **wszystkie programy**  > **Microsoft Visual Studio 2010 SDK**  > **Narzędzia**  > **Zresetuj wystąpienie eksperymentalne**.

11. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**.

## <a name="see-also"></a>Zobacz także

[Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)