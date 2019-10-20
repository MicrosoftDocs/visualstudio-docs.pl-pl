---
title: 'Instrukcje: Tworzenie lub aktualizowanie standardowych zasad zaewidencjonowania analizy kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661776"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Porady: tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można wymagać, aby analiza kodu była uruchamiana we wszystkich projektach kodu w projekcie zespołowym za pomocą zasad ewidencjonowania analizy kodu. Wymaganie analizy kodu może poprawić jakość kodu, który jest sprawdzany w bazie kodu.

> [!NOTE]
> Ta funkcja jest dostępna tylko wtedy, gdy używasz Team Foundation Server.

 Zasady ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu zespołowego i stosowane do każdego projektu kodu w projekcie zespołowym. Przebiegi analizy kodu są skonfigurowane dla projektów kodu w pliku projektu (. xxproj) dla projektu kodu. Uruchomienia analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad zaewidencjonowania analizy kodu, pliki w projekcie kodu, które mają być zaewidencjonowane, muszą być kompilowane po ostatniej edycji i przebiegu analizy kodu, który zawiera, co najmniej reguły w ustawieniach projektu zespołowego muszą być wykonywane na komputerze, na którym c zawieszeń.

- Dla kodu zarządzanego ustawia się zasady ewidencjonowania, określając *zestaw reguł* , który zawiera podzbiór reguł analizy kodu.

- W przypadku językaC++ C/Code zasady ewidencjonowania wymagają uruchomienia wszystkich reguł analizy kodu. Można dodać dyrektywy poprzedzające procesor, aby wyłączyć określone reguły dla poszczególnych projektów kodu w projekcie zespołowym.

  Po określeniu zasad ewidencjonowania dla kodu zarządzanego członkowie zespołu mogą synchronizować swoje ustawienia analizy kodu dla projektów kodu z ustawieniami zasad projektu zespołowego.

### <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania

1. W Team Explorer kliknij prawym przyciskiem myszy nazwę projektu zespołowego, wskaż **Ustawienia projektu zespołowego**, a następnie kliknij pozycję **Kontrola źródła**.

2. W oknie dialogowym **Kontrola źródła** wybierz kartę **zasady ewidencjonowania** .

3. Wykonaj jedną z następujących czynności:

    - Kliknij przycisk **Dodaj** , aby utworzyć nowe zasady ewidencjonowania.

    - Kliknij dwukrotnie istniejący element **analizy kodu** na liście **Typ zasad** , aby zmienić zasady.

### <a name="to-set-policy-options"></a>Aby ustawić opcje zasad

- Zaznacz lub usuń zaznaczenie następujących opcji:

    |Opcja|Opis|
    |------------|-----------------|
    |**Wymuś zaewidencjonowanie tylko do plików, które są częścią bieżącego rozwiązania.**|Analiza kodu może być uruchamiana tylko na plikach określonych w plikach konfiguracji rozwiązania i projektu. Ta zasada gwarantuje, że jest analizowany cały kod, który jest częścią rozwiązania.|
    |**Wymuś analizę koduC++ C/Code (/analyze)**|Wymaga, aby wszystkie C C++ lub projekty zostały skompilowane przy użyciu opcji kompilatora/Analyze, aby uruchomić analizę kodu, zanim będzie można je zaewidencjonować.|
    |**Wymuszaj analizę kodu dla kodu zarządzanego**|Wymaga, aby wszystkie zarządzane projekty wykonywały analizę kodu i kompilację, zanim będzie można je zaewidencjonować.|

-

### <a name="to-specify-a-managed-rule-set"></a>Aby określić zarządzany zestaw reguł

- Z listy **Uruchom ten zestaw reguł** Użyj jednej z następujących metod:

  - Wybierz standardowy zestaw reguł firmy Microsoft.

  - Aby wybrać niestandardowy zestaw reguł, kliknij pozycję **\<Select zestaw reguł z kontroli źródła... >** , a następnie wpisz ścieżkę kontroli wersji zestawu reguł w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Aby uzyskać więcej informacji na temat sposobu tworzenia i implementowania niestandardowego zestawu reguł zaewidencjonowania, zobacz [implementowanie niestandardowych zasad ewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Zobacz też
 [Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
