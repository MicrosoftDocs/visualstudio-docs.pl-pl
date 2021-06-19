---
title: Jak zmienić przestrzeń nazw języka specyficznego dla domeny
description: Zawiera informacje na temat sposobu zmiany przestrzeni nazw języka specyficznego dla domeny.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: db9043c2a4c5abd19c839d2586709412d7607019
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387310"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Jak zmienić przestrzeń nazw języka specyficznego dla domeny

Przestrzeń nazw języka specyficznego dla domeny można zmienić. Zmień w eksploratorze **DSL**, we właściwościach projektu Dsl Package i w informacjach o zestawie.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Aby zmienić przestrzeń nazw języka specyficznego dla domeny

1. W **Eksploratorze DSL** wybierz **węzeł Dsl.**

2. W **oknie** Właściwości zmień właściwość **Przestrzeń** nazw.

3. Zapisz rozwiązanie i przekształć szablony.

4. W menu **Project (Projekt)** wybierz pozycję **Dsl Properties (Właściwości DSL).**

   Zostaną wyświetlone właściwości projektu.

5. Wybierz **kartę** Aplikacja.

6. Zmień właściwość **Domyślna przestrzeń** nazw na nową nazwę przestrzeni nazw.

7. Jeśli chcesz również zmienić nazwę zestawu, zmień właściwość **Nazwa zestawu.**

8. Jeśli zmieniono nazwę zestawu, otwórz folder DslPackage\Package.tt zaktualizuj ten wiersz:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Jeśli został napisany dowolny kod niestandardowy, pamiętaj, aby zmienić odwołania do przestrzeni nazw i klas w plikach kodu.

10. Zresetuj Visual Studio eksperymentalne.

    1. Usuń **\Users \\**_{Twoja nazwa}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**.

    2. W menu **Start systemu** Windows wybierz pozycję **Wszystkie** programy Microsoft Visual Studio  >  **2010 SDK** Tools  >  **Reset** the Experimental Instance  >  (Zresetuj **wystąpienie eksperymentalne).**

11. W menu **Kompilacja** wybierz pozycję **Odbuduj rozwiązanie.**

## <a name="see-also"></a>Zobacz też

[Słownik narzędzi językowych specyficznych dla domeny](/previous-versions/bb126564(v=vs.100))