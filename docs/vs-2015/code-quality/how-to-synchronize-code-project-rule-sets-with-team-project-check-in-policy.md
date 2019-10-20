---
title: 'Instrukcje: synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651597"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Porady: synchronizowanie zestawu reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia analizy kodu dla projektów kodu są synchronizowane z zasadami ewidencjonowania projektu zespołowego przez określenie zestawu reguł, który zawiera co najmniej reguły, które są określone w zestawie reguł dla zasad ewidencjonowania. Lider deweloperów może poinformować użytkownika o nazwie i lokalizacji zestawu reguł dla zasad ewidencjonowania. Możesz użyć jednej z następujących opcji, aby upewnić się, że analiza kodu dla projektu korzysta z poprawnego zestawu reguł:

- Jeśli zasady ewidencjonowania korzystają z jednego z wbudowanych zestawów reguł firmy Microsoft, Otwórz okno dialogowe właściwości dla projektu kodu, Wyświetl stronę Analiza kodu i wybierz regułę ustawioną na stronie Analiza kodu w ustawieniach projektu kodu. Standardowe zestawy reguł firmy Microsoft są automatycznie instalowane z programem Visual Studio i nie powinny być edytowane. Jeśli zestawy reguł nie są edytowane, zasady dotyczące zasad i lokalnych zestawów reguł są gwarantowane.

- Jeśli zasady ewidencjonowania korzystają z niestandardowego zestawu reguł, należy wykonać operację pobierania w pliku zestawu reguł w kontroli wersji, aby utworzyć kopię lokalną. Następnie określ tę lokalizację lokalną w ustawieniach analizy kodu dla projektu kodu. Reguły są gwarantowane, jeśli zestaw reguł dla zasad ewidencjonowania jest aktualny.

     W przypadku mapowania lokalizacji kontroli wersji do folderu lokalnego, który znajduje się w tej samej relacji do katalogu głównego projektu zespołowego jako projektu kodu, lokalizacja reguły jest ustawiana za pomocą ścieżki względnej. Ścieżka względna zapewnia, że ustawienie projektu kodu dla analizy kodu można przenieść na inne komputery.

- Dostosuj kopię zestawu reguł dla zasad ewidencjonowania dla projektu kodu. Upewnij się, że nowy zestaw reguł zawiera wszystkie reguły w zasadach ewidencjonowania oraz inne reguły, które chcesz dołączyć. Należy upewnić się, że zestaw reguł zawiera wszystkie reguły w zestawie reguł dla zasad ewidencjonowania.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Aby określić standardowy zestaw reguł firmy Microsoft

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **Analiza kodu**.

3. Na liście **Uruchom ten zestaw reguł** kliknij zestaw reguł zaewidencjonowania.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Aby określić niestandardowy zestaw reguł ewidencjonowania

1. W razie potrzeby wykonaj operację Pobierz w pliku zestawu reguł, który określa zasady ewidencjonowania.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

3. Kliknij pozycję **Analiza kodu**.

4. Na liście **Uruchom ten zestaw reguł** kliknij **\<Browse... >** .

5. W oknie dialogowym **otwieranie** Określ plik zestawu reguł ewidencjonowania.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Aby utworzyć niestandardowy zestaw reguł dla projektu kodu

1. Wykonaj jedną z procedur znajdujących się we wcześniejszej części tego tematu, aby wybrać zasady zaewidencjonowania projektu zespołowego na stronie Analiza kodu w oknie dialogowym Ustawienia projektu.

2. Kliknij przycisk **Otwórz**.

3. Dodawanie lub usuwanie reguł za pomocą edytora zestawu reguł.

     Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Zapisz zmodyfikowany zestaw reguł na pliku. zestawu reguł na komputerze lokalnym lub w ścieżce UNC.

5. Otwórz okno dialogowe właściwości dla projektu kodu i Wyświetl stronę **Analiza kodu** .

6. Na liście **Uruchom ten zestaw reguł** kliknij **\<Browse... >** .

7. W **Otwórz** okno dialogowe, określ plik zestawu reguł.
