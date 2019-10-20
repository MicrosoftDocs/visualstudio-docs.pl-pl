---
title: Pomijanie naruszeń analizy kodu dla wygenerowanego kodu
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39daa50254f2d1b69514d4065e582154e9ceb6b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649395"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Instrukcje: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu

Wygenerowany kod zawiera kod, który jest dodawany do projektu przez kompilatory kodu zarządzanego lub narzędzia innych firm. Warto zapoznać się z naruszeniami reguł, które są wykrywane przez analizę kodu w wygenerowanym kodzie. Jednak ponieważ nie można wyświetlić i zachować kodu, który zawiera naruszenia, może nie chcieć ich zobaczyć.

Pole wyboru **Pomiń wyniki z wygenerowanego kodu** na stronie właściwości Analiza kodu projektu umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu wygenerowanego przez narzędzie innej firmy.

> [!NOTE]
> Ta opcja nie powoduje pomijania błędów analizy kodu i ostrzeżeń z wygenerowanego kodu, gdy błędy i ostrzeżenia pojawiają się w formularzach i szablonach. Można zarówno wyświetlać, jak i konserwować kod źródłowy formularza lub szablonu.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżenia dla wygenerowanego kodu w projekcie

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie kliknij polecenie **Właściwości**.

2. Wybierz kartę **Analiza kodu** .

3. Zaznacz pole wyboru **Pomiń wyniki z wygenerowanego kodu** .

> [!NOTE]
> Można pominąć tylko ostrzeżenia ze starszej wersji analizy. Obecnie nie można pominąć ostrzeżeń analizy kodu z [analizatorów](roslyn-analyzers-overview.md).
