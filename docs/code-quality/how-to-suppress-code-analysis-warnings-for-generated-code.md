---
title: 'Instrukcje: Pomijanie ostrzeżeń analizy wygenerowanego kodu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2913ea1645ab7fced11aa64e671a5c0f0a87edc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844983"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Instrukcje: Pomijanie ostrzeżeń analizy wygenerowanego kodu
Kompilatory kodu zarządzanego często generują kod, który jest dodawany do projektu w celu ułatwienia tworzenia kodu szybkiego. Ponadto deweloperzy często używają narzędzi innych firm ułatwia szybkie tworzenie aplikacji. Te narzędzia są również wygenerować kod, który jest dodawany do projektu.

 Możesz chcieć wyświetlić naruszenia reguły, które analizy kodu, który umożliwia odnalezienie w wygenerowanym kodzie. Jednak możesz nie chcieć je wyświetlić, jeśli nie można wyświetlić i utrzymywać kod, który zawiera naruszenie.

 **Pomijaj wyniki z wygenerowanego kodu** pole wyboru na stronie właściwości analizy kodu projektu umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu w kodzie wygenerowanym przez narzędzie innej firmy.

> [!NOTE]
>  Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można wyświetlać lub zachować kod źródłowy dla formularza lub szablonu.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżeń dla wygenerowanego kodu w projekcie

1.  Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.

2.  Kliknij przycisk **analiza kodu**.

3.  Wybierz **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.