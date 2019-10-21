---
title: 'Instrukcje: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646278"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Porady: pomijanie ostrzeżeń analizy kodu dla wygenerowanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kompilatory kodu zarządzanego często generują kod, który jest dodawany do projektu w celu ułatwienia szybkiego tworzenia kodu. Ponadto deweloperzy często używają narzędzi innych firm, aby szybko opracowywać aplikacje. Narzędzia te generują również kod, który jest dodawany do projektu.

 Warto zapoznać się z naruszeniami reguł, które są wykrywane przez analizę kodu w wygenerowanym kodzie. Niemniej jednak, jeśli nie możesz wyświetlić i zachować kodu, który zawiera naruszenie.

 Pole wyboru **Pomiń wyniki z wygenerowanego kodu** na stronie właściwości Analiza kodu projektu umożliwia wybranie, czy chcesz zobaczyć ostrzeżenia analizy kodu z kodu wygenerowanego przez narzędzie innej firmy.

> [!NOTE]
> Ta opcja nie powoduje pomijania błędów analizy kodu i ostrzeżeń z wygenerowanego kodu, gdy błędy i ostrzeżenia pojawiają się w formularzach i szablonach. Można zarówno wyświetlać, jak i konserwować kod źródłowy formularza lub szablonu.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Aby pominąć ostrzeżenia dla wygenerowanego kodu w projekcie

1. Kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **Analiza kodu**.

3. Zaznacz pole wyboru **Pomiń wyniki z wygenerowanego kodu** .
