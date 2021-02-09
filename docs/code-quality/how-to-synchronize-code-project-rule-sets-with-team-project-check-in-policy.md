---
title: Synchronizowanie zestawów reguł projektu z zasadami ewidencjonowania
ms.date: 11/04/2016
description: Dowiedz się, jak zsynchronizować zestaw reguł projektu programu Visual Studio Code z zasadami ewidencjonowania projektu usługi Azure DevOps.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2908f7ec93d8704b52798121bd0076a7f5fddc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859921"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Instrukcje: synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu usługi Azure DevOps

Ustawienia analizy kodu dla projektów kodu można synchronizować z zasadami ewidencjonowania dla projektu usługi Azure DevOps, określając zestaw reguł, który zawiera co najmniej reguły, które są określone w zestawie reguł dla zasad ewidencjonowania. Lider deweloperów może poinformować użytkownika o nazwie i lokalizacji zestawu reguł dla zasad ewidencjonowania. Możesz użyć jednej z następujących opcji, aby upewnić się, że analiza kodu dla projektu korzysta z poprawnego zestawu reguł:

- Jeśli zasady ewidencjonowania korzystają z jednego z wbudowanych zestawów reguł firmy Microsoft, Otwórz okno dialogowe właściwości dla projektu kodu, Wyświetl stronę Analiza kodu i wybierz zestaw reguł. Standardowe zestawy reguł firmy Microsoft są automatycznie instalowane z programem Visual Studio i nie powinny być edytowane. Jeśli zestawy reguł nie są edytowane, zasady dotyczące zasad i lokalnych zestawów reguł są gwarantowane.

- Jeśli zasady ewidencjonowania korzystają z niestandardowego zestawu reguł, należy wykonać operację pobierania w pliku zestawu reguł w kontroli wersji, aby utworzyć kopię lokalną. Następnie określ tę lokalizację lokalną w ustawieniach analizy kodu dla projektu kodu. Reguły są gwarantowane, jeśli zestaw reguł dla zasad ewidencjonowania jest aktualny.

     W przypadku mapowania lokalizacji kontroli wersji do folderu lokalnego, który znajduje się w tej samej relacji do katalogu głównego projektu usługi Azure DevOps jako projektu kodu, lokalizacja reguły jest ustawiana za pomocą ścieżki względnej. Ścieżka względna zapewnia, że ustawienie projektu kodu dla analizy kodu można przenieść na inne komputery.

- Dostosuj kopię zestawu reguł dla zasad ewidencjonowania dla projektu kodu. Upewnij się, że nowy zestaw reguł zawiera wszystkie reguły w zasadach ewidencjonowania oraz inne reguły, które chcesz dołączyć. Należy upewnić się, że zestaw reguł zawiera wszystkie reguły w zestawie reguł dla zasad ewidencjonowania.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Aby określić standardowy zestaw reguł firmy Microsoft

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **Analiza kodu**.

::: moniker range="vs-2017"

3. Na liście **Uruchom ten zestaw reguł** wybierz zestaw reguł zaewidencjonowania.

::: moniker-end

::: moniker range=">=vs-2019"

3. Na liście **aktywne reguły** wybierz zestaw reguł zaewidencjonowania.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Aby określić niestandardowy zestaw reguł ewidencjonowania

1. W razie potrzeby wykonaj operację Pobierz w pliku zestawu reguł, który określa zasady ewidencjonowania.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

3. Kliknij pozycję **Analiza kodu**.

::: moniker range="vs-2017"

4. Na liście **Uruchom ten zestaw reguł** kliknij pozycję **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Na liście **aktywne reguły** kliknij pozycję **\<Browse>** .

::: moniker-end

5. W oknie dialogowym **otwieranie** Określ plik zestawu reguł ewidencjonowania.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Aby utworzyć niestandardowy zestaw reguł dla projektu kodu

Aby uzyskać informacje na temat tworzenia niestandardowego zestawu reguł, zobacz [Dostosowywanie zestawu reguł](how-to-create-a-custom-rule-set.md).
