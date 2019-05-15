---
title: Pomija analizę kodu naruszenia wygenerowany kod
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613573"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Instrukcje: Pomijanie ostrzeżeń analizy wygenerowanego kodu

Wygenerowany kod zawiera kod, który jest dodawany do projektu kodu zarządzanego, kompilatory lub narzędzi innych firm. Możesz chcieć wyświetlić naruszenia reguły, które analizy kodu, który umożliwia odnalezienie w wygenerowanym kodzie. Jednak ponieważ nie można wyświetlić, a Obsługa kodu, który zawiera naruszenia, nie można je wyświetlić.

**Pomijaj wyniki z wygenerowanego kodu** pole wyboru na stronie właściwości analizy kodu projektu umożliwia wybranie, czy ma być wyświetlana kod ostrzeżenia analizy w kodzie wygenerowanym przez narzędzie innej firmy.

> [!NOTE]
> Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można wyświetlać lub zachować kod źródłowy dla formularza lub szablonu.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżeń dla wygenerowanego kodu w projekcie

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** a następnie kliknij przycisk **właściwości**.

2. Wybierz **analizy kodu** kartę.

3. Wybierz **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

> [!NOTE]
> Można tylko pomijanie ostrzeżeń analizy kodu statycznego. Obecnie nie można pominąć ostrzeżenia analizy kodu z [analizatory](roslyn-analyzers-overview.md).