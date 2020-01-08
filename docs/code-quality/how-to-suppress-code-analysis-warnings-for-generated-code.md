---
title: Pomijanie naruszeń analizy kodu dla wygenerowanego kodu
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab2ffce28103059414cef8f1b556152485a12ff
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587436"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Instrukcje: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu

Wygenerowany kod zawiera kod, który jest dodawany do projektu przez kompilatory kodu zarządzanego lub narzędzia innych firm. Warto zapoznać się z naruszeniami reguł, które są wykrywane przez analizę kodu w wygenerowanym kodzie. Jednak ponieważ nie można wyświetlić i zachować kodu, który zawiera naruszenia, może nie chcieć ich zobaczyć.

Pole wyboru **Pomiń wyniki z wygenerowanego kodu** na stronie właściwości Analiza kodu projektu umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu wygenerowanego przez narzędzie innej firmy.

> [!NOTE]
> Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można zarówno wyświetlać, jak i konserwować kod źródłowy formularza lub szablonu.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżenia dla wygenerowanego kodu w projekcie

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie kliknij polecenie **Właściwości**.

2. Wybierz kartę **Analiza kodu** .

3. Zaznacz pole wyboru **Pomiń wyniki z wygenerowanego kodu** .

> [!IMPORTANT]
> Można pominąć tylko ostrzeżenia ze starszej wersji analizy. Strona właściwości z ustawieniem jest przestarzała i zostanie usunięta w przyszłej wersji produktu. Obecnie nie można pominąć ostrzeżeń analizy kodu z [analizatorów](roslyn-analyzers-overview.md).
