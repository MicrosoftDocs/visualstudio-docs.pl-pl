---
title: Tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11f64d2776b0d442d074c99c82287f1e7c482f1e
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506506"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Porady: tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu

Można wymagać uruchamiania analizy kodu dla wszystkich projektów kodu w projekcie usługi Azure DevOps za pomocą zasad ewidencjonowania analizy kodu. Wymaganie analizy kodu może poprawić jakość kodu, który jest sprawdzany w bazie kodu.

> [!NOTE]
> Ta funkcja jest dostępna tylko wtedy, gdy używasz Team Foundation Server.

Zasady ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu i stosowane do każdego projektu kodu. Przebiegi analizy kodu są skonfigurowane dla projektów kodu w pliku projektu (. xxproj) dla projektu kodu. Uruchomienia analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad zaewidencjonowania analizy kodu, pliki w projekcie kodu, które mają być zaewidencjonowane, muszą być kompilowane po ostatniej edycji i przebiegu analizy kodu, który zawiera, co najmniej reguły w ustawieniach projektu muszą zostać wykonane na komputerze, na którym zmiana zostały wykonane.

- Dla kodu zarządzanego ustawia się zasady ewidencjonowania, określając *zestaw reguł* , który zawiera podzbiór reguł analizy kodu.

- W przypadku językaC++ C/Code w programie Visual Studio 2017 w wersji 15,6 lub starszej zasady ewidencjonowania wymagają uruchomienia wszystkich reguł analizy kodu. Można dodać dyrektywy poprzedzające procesor, aby wyłączyć określone reguły dla poszczególnych projektów kodu w projekcie usługi Azure DevOps. W 15,7 i nowszych można użyć **/analyze:** Rule, aby określić, które reguły mają być uruchamiane. Aby uzyskać więcej informacji, zobacz [używanie zestawów reguł do określania C++ reguł do uruchomienia](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

Po określeniu zasad ewidencjonowania dla kodu zarządzanego członkowie zespołu mogą synchronizować swoje ustawienia analizy kodu dla projektów kodu z ustawieniami zasad projektu usługi Azure DevOps.

## <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania

1. W Team Explorer kliknij prawym przyciskiem myszy nazwę projektu, wskaż polecenie **Ustawienia projektu**, a następnie kliknij pozycję **Kontrola źródła**.

1. W oknie dialogowym **Kontrola źródła** wybierz kartę **zasady ewidencjonowania** .

1. Wykonaj jedną z następujących czynności:

    - Kliknij przycisk **Dodaj** , aby utworzyć nowe zasady ewidencjonowania.

    - Kliknij dwukrotnie istniejący element **analizy kodu** na liście **Typ zasad** , aby zmienić zasady.

## <a name="to-set-policy-options"></a>Aby ustawić opcje zasad

Zaznacz lub usuń zaznaczenie następujących opcji:

|Opcja|Opis|
|------------|-----------------|
|**Wymuś zaewidencjonowanie tylko do plików, które są częścią bieżącego rozwiązania.**|Analiza kodu może być uruchamiana tylko na plikach określonych w plikach konfiguracji rozwiązania i projektu. Ta zasada gwarantuje, że jest analizowany cały kod, który jest częścią rozwiązania.|
|**Wymuś analizę koduC++ C/Code (/analyze)**|Wymaga, aby wszystkie C C++ lub projekty zostały skompilowane przy użyciu opcji kompilatora/Analyze, aby uruchomić analizę kodu, zanim będzie można je zaewidencjonować.|
|**Wymuszaj analizę kodu dla kodu zarządzanego**|Wymaga, aby wszystkie zarządzane projekty wykonywały analizę kodu i kompilację, zanim będzie można je zaewidencjonować.|

## <a name="to-specify-a-managed-rule-set"></a>Aby określić zarządzany zestaw reguł

Z listy **Uruchom ten zestaw reguł** Użyj jednej z następujących metod:

- Wybierz standardowy zestaw reguł firmy Microsoft.

- Wybierz zestaw reguł niestandardowych, klikając **\<wybierz zestaw reguł z kontroli źródła... >** . Następnie wpisz ścieżkę kontroli wersji zestawu reguł w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Aby uzyskać więcej informacji na temat sposobu tworzenia i implementowania niestandardowego zestawu reguł zaewidencjonowania, zobacz [implementowanie niestandardowych zasad ewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Zobacz też

- [Implementowanie niestandardowych zasad ewidencjonowania analizy kodu dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
