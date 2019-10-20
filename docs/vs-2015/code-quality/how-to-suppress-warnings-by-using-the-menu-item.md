---
title: 'Instrukcje: pomijanie ostrzeżeń przy użyciu elementu menu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610014"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Porady: tłumienie ostrzeżeń przy użyciu elementu menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> W przypadku pomijania źródła nie jest obsługiwane dla projektów witryny sieci Web.

 Możesz użyć okna analizy kodu, aby pominąć ostrzeżenia analizy kodu. Pomijanie ostrzeżenia nie jest takie samo jak wyłączenie. Pomijanie ostrzeżenia dotyczy tylko określonego wystąpienia naruszenia. Inne naruszenia tego samego ostrzeżenia będą nadal raportowane w oknie Lista błędów.

 Po uruchomieniu analizy kodu można określić, że co najmniej jedno ostrzeżenie analizy kodu, które są wyświetlane w oknie analizy kodu, nie ma zastosowania do aplikacji. Można na przykład określić, że kod jest poprawny w zależności od tego. Może się też zdarzyć, że niektóre naruszenia mają niski priorytet i nie zostaną naprawione w bieżącym cyklu tworzenia oprogramowania. Niezależnie od przyczyny, często warto wskazać, że ostrzeżenie nie ma zastosowania, aby umożliwić członkom zespołu znać, że kod został zweryfikowany i że został ustalony, że ostrzeżenie może zostać pominięte. W przypadku pomijania źródła jest to przydatne, ponieważ umożliwia umieszczenie pomijania w pobliżu miejsca, w którym jest generowane ostrzeżenie.

 Możesz wybrać, czy pomijanie będzie widoczne w kodzie źródłowym, czy w globalnym pliku do pomijania. Niektóre pominięcia muszą zostać umieszczone w globalnym pliku do pomijania. W takim przypadku opcja **w źródle** zostanie wyłączona.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Aby pominąć ostrzeżenie przy użyciu elementu menu

1. W menu **Analizuj** wybierz pozycję **Windows** , a następnie wybierz pozycję **Analiza kodu**.

2. W oknie **Analiza kodu** wybierz Pomijanie ostrzeżenia.

3. Wybierz pozycję akcje, a następnie wybierz pozycję **Pomiń komunikaty**, a następnie wybierz pozycję **w polu Źródło** lub **w pliku pomijania projektu**.

     Określone ostrzeżenie jest pomijane, a w oknie Analiza kodu zostanie wyświetlone ostrzeżenie z przekreśleniem.

> [!NOTE]
> Pominięcia, które nie mają elementu docelowego pojawiają się w globalnym pliku pomijania.
