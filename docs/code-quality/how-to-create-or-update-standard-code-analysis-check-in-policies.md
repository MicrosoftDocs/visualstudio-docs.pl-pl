---
title: Tworzenie lub aktualizowanie standardowych zasad analizy kodu zaewidencjonowania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a74926f4fd9136e15757eb6967d5eb56a8ecbf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890342"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Instrukcje: Tworzenie lub aktualizowanie standardowych zasad analizy kodu zaewidencjonowania

Możesz wymagać, można uruchomić analizę kodu dla wszystkich projektów kodu w projekcie DevOps platformy Azure w przy użyciu zasady analizy kodu ewidencjonowania. Wymaga analizy kodu może poprawić jakość kodu, który jest ewidencjonowany w kodzie podstawowym.

> [!NOTE]
> Ta funkcja jest dostępna tylko wtedy, gdy używasz Team Foundation Server.

Zasady ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu i mają zastosowanie do każdego projektu kodu. Przebiegi analizy kodu są skonfigurowane dla projektów kodu w pliku projektu (.xxproj) dla projektu kodu. Przebiegi analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad analizy kodu ewidencjonowania, muszą być skompilowane pliki w projekcie kodu, które mają być sprawdzane po ich ostatniej modyfikacji i uruchomienia analizy kodu zwrócić, zawiera co najmniej reguły w ustawieniach projektu odbywa się na komputerze, gdzie zmiany wprowadzono s.

- Dla kodu zarządzanego, Ustaw zasady ewidencjonowania, określając *zestaw reguł* zawierającą podzbiór reguł analizy kodu.

- Dla kodu C/C++ w programie Visual Studio 2017 w wersji 15.6 i starszych wersjach zasad ewidencjonowania wymaga, że są uruchomione wszystkie reguły analizy kodu. Możesz dodać wstępne procesora dyrektywy można wyłączyć określone zasady dla poszczególnych projektów kodu projektu DevOps platformy Azure. W wersji 15.7 lub nowszej, możesz użyć **/ analyze: ruleset** Aby określić, które reguł do uruchomienia. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów reguł do określania reguł C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Po określeniu zasad ewidencjonowania dla kodu zarządzanego, członkowie zespołu mogą wykonywać synchronizację z ich ustawienia analizy kodu dla projektów kodu do ustawień zasad projektu DevOps platformy Azure.

## <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania

1. W programie Team Explorer, kliknij prawym przyciskiem myszy nazwę projektu, wskaż opcję **ustawienia projektu**, a następnie kliknij przycisk **kontroli źródła**.

1. W **kontroli źródła** okno dialogowe, wybierz opcję **zasad ewidencjonowania** kartę.

1. Wykonaj jedną z następujących czynności:

    - Kliknij przycisk **Dodaj** do tworzenia nowych zasad ewidencjonowania.

    - Kliknij dwukrotnie istniejące **analizy kodu** pozycja **typ zasad** listy, aby zmienić zasady.

## <a name="to-set-policy-options"></a>Aby ustawić opcje zasad

Zaznacz lub wyczyść następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Wymuszanie zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania.**|Analiza kodu można uruchomić tylko na pliki określone w plikach konfiguracji rozwiązania i projektu. Te zasady gwarantuje, że cały kod, który jest częścią rozwiązania są analizowane.|
|**Wymuszanie analiza kodu C/C++ (/ analyze)**|Wymaga się, że wszystkie projekty C lub C++ być kompilowany / analyze — opcja kompilatora do uruchamiania analizy kodu, zanim może zostać sprawdzone.|
|**Wymuszanie analizy kodu dla kodu zarządzanego**|Wymaga wszystkich zarządzanych projektów uruchamiania analizy kodu i kompilacji, zanim może zostać sprawdzone.|

## <a name="to-specify-a-managed-rule-set"></a>Aby określić zestaw reguł zarządzanych

Z **Uruchom ten zestaw reguł** listy, użyj jednej z następujących metod:

- Wybierz zestaw standardowych reguł firmy Microsoft.

- Wybierz niestandardową regułę, ustaw, klikając  **\<wybierz zestaw reguł z kontroli źródła... >**. Następnie wpisz ścieżkę kontroli wersji, reguły, ustaw w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Aby uzyskać więcej informacji o sposobie tworzenia i wdrażania reguły niestandardowe zasady ewidencjonowania, zobacz [Implementowanie niestandardowych zaewidencjonowania zasad dla zarządzanego kodu](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zasad ewidencjonowania analizy kodu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)